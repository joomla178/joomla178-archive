---
title: "Joomla! 搜索字符限制解决方案"
source: "http://www.joomla178.com/joomla-share/research-and-development/joomla-search-limit-word-solution.html"
category: "研究开发"
author: "Jiang"
date: "2013-06-18"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla! 搜索字符限制解决方案

由于中文不同英文，大家在搜索中文的时候通常都是搜索1个及1个以上的字符，但是我们知道在Joomla! 1.5时代，在使用Joomla! 1.5的搜索时，
如果只输入了一个字 ，在搜索结果中就会得到这样的提示：关键词最少3个字符，最多20个字符。包括现在的Joomla! 2.5及Joomla! 3 都会有此问题，我们之前有针对Joomla! 1.5做的解决方案：[joomla常见问题解决方案](27.md) 。

那么其实官方团队在做Joomla! 2.5的时候已经改善了这个问题的存在，只不过考虑不同国家地区的情况不一样，所以没有一个统一标准，仍然保留了英文默认的3个字符的搜索条件，然后在各国的语言包中，官方团队留下了一个完美的解决方案，只不过汉化团队目前仍未利用此方案。

我们知道在安装台版的繁体中文语言包时，前台搜索输入1个字符的时候，会得到这样的提示：搜尋字詞最少 2 個字元，最多 20 個字元，也就充分说明了Joomla! 字符搜索的限制并不像Joomla! 1.5那样修改核心代码，而是修改语言的相关文件。

说了这么多旨在让朋友知道开发团队的用意，那么这个新东西其实大家很容易忽略它，它的位置就在/language/zh-CN/zh-CN.localise.php，这是官方开发团队在语言包中新增的一个语言调剂文件，用于不同语言的差异化解决方案，打开文件，我们注意以下三段代码：

```
public static function getLowerLimitSearchWord() {	return 3;
}public static function getUpperLimitSearchWord() {	return 20;
}public static function getSearchDisplayedCharactersNumber() {	return 200;
}
```

不言而喻，第一个函数是表示返回搜索的最少字符数，第二个函数表示返回的最大字符数，第三个函数表示返回搜索结果的相关正文最大字符数。

按照我们的需求将第一个函数的return值的3改为1，这样就可以搜索一个字符了，当然第三个函数还可以改成100，避免页面过长。

我们希望的是官方的汉化语言包默认就可以支持1个字符的搜索，本文写于当前的Joomla! 2.5.11 版本，至此笔者已联络官方的汉化团队有关此事，希望在下一个版本的汉化语言包中修改此问题。

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla! 搜索字符限制解决方案](http://www.joomla178.com/joomla-share/research-and-development/joomla-search-limit-word-solution.html)
