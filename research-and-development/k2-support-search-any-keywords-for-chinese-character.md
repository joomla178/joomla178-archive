---
title: "让K2完美支持搜索任意长度的中文字符"
source: "http://www.joomla178.com/joomla-share/research-and-development/k2-support-search-any-keywords-for-chinese-character.html"
category: "研究开发"
author: "Jiang"
date: "2011-12-05"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 让K2完美支持搜索任意长度的中文字符

我们以前讲过K2的标题字符限制教程：[定制了一下mod\_k2\_content，符合中文使用习惯的限制标题字数](72.md)，那次是为了让PHP支持限定中文字符，那么K2搜索中文的方式和Joomla自带文章搜索中文方式不同！主要表现在SQL查询语句方式不同，Joomla任意关键词搜索主要是用到SQL语句中的LIKE条件句，而K2的任意关键词SQL查询语句的条件句是MATCH (title,body) AGAINST ('keyword')（一种全文搜索方式）方式，后者K2的SQL语句对中文支持不太好，详情我就不多讲了，那么我们在这里就需要把K2的搜索查询语句的条件句换成LIKE。

安装K2之后，会附带安装了一个名为Search-K2的插件，这个插件有两个文件，位于**\plugins\search\**目录下

打开**\plugins\search\k2.php**找到代码：

```
else {	$text = JString::str_ireplace('*', '', $text);	$words = explode(' ', $text);	for($i=0; $i<count($words); $i++){		if($phrase=='all')		$words[$i]= '+'.$words[$i];		$words[$i].= '*';		}	$text = implode(' ', $words);	$text = $db->Quote($db->getEscaped($text, true), false);	}
```

修改为以下代码（本步骤是去除了K2原有的复杂获取关键词方式，并给关键词设置格式：'%关键词%'）

```
else {	$words = explode(' ', $text);	$text = implode(' ', $words);	$text = $db->Quote('%'.$db->getEscaped($text, true).'%', false);	}
```

再找到以下SQL查询语句的条件句部分，

```
WHERE (";	if($pluginParams->get('search_tags') && count($itemIDs)){		JArrayHelper::toInteger($itemIDs);		$query.=" i.id IN (".implode(',',$itemIDs).") OR ";	}	$query.="MATCH(i.title, i.introtext, i.`fulltext`,i.extra_fields_search,i.image_caption,i.image_credits,i.video_caption,i.video_credits,i.metadesc,i.metakey) AGAINST ({$text} IN BOOLEAN MODE))
```

改为（注意上述WHERE后面的括号已经去掉了）：

```
WHERE i.title LIKE $text		OR i.introtext LIKE $text		OR i.`fulltext` LIKE $text		OR i.extra_fields_search LIKE $text		OR i.image_caption LIKE $text		OR i.image_credits LIKE $text		OR i.video_caption LIKE $text		OR i.video_credits LIKE $text		OR i.metadesc LIKE $text		OR i.metakey LIKE $text
```

保存文件即可，当然注意保存原文件的备份哦。本修改会随着K2的版本升级而还原，也请注意保存修改后的文件。

**原创文章转载请标明出处，请引用本文地址：**[让K2完美支持搜索任意长度的中文字符](k2-support-search-any-keywords-for-chinese-character.md)

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [让K2完美支持搜索任意长度的中文字符](http://www.joomla178.com/joomla-share/research-and-development/k2-support-search-any-keywords-for-chinese-character.html)
