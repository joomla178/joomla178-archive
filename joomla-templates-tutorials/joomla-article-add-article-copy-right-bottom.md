---
title: "Joomla!文章底部添加版权转载说明"
source: "http://www.joomla178.com/joomla-share/joomla-templates-tutorials/joomla-article-add-article-copy-right-bottom.html"
category: "JOOMLA模板开发"
author: ""
date: "2013-04-15"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla!文章底部添加版权转载说明

在有的博客中有这样的功能或者插件，文章结束处有说明文章版权说明，类似 **本文链接地址:http://www.Joomla178.com/，转摘请注明出处**  的字样，应该是有这样的插件，不过在[Joomla!](http://www.Joomla178.com/) 中DIY方法实现起来非常简单。

在DIY之前我们务必要看看之前有说过配置文章布局的相关文章：[Joomla! 2.5.x 文章布局、分类布局模板释疑](joomla25-article-layout-and-blog-layout.md)，按文中办法创建一个新的文章模板，避免因升级造成的DIY丢失。

弄清[Joomla!](http://www.Joomla178.com/) 的文章模板的结构之后，事情变得简单了

**一步搞定，建立一个文章模板，添加代码**

以JOOMLA178模板为例，复制文件**/components/com\_content/views/article/tmpl/default.php**至**/template/jk\_Joomla178/html/content/article/default.php** 打开该文件，找到代码：

```php
<?php echo $this->item->text; ?>
```

在其后面添加代码后就是：

```php
<?php echo $this->item->text; ?><div class="link_notice"><?php echo JText::_('原创文章，转载请保留本文链接：'); ?>	<a href="/<?php echo $this->item->readmore_link; ?>">		<?php echo $this->item->title; ?>	</a></div>
```

解释一下，原理就是在文章结尾处，添加一段自定义内容：一置方法JText::\_输出声明内容+带链接的标题，声明内容就是代码中的“**原创文章，转载请保留本文链接：**”链接代码则是$this->item->readmore\_link;，当前文章标题就是$this->item->title;，依次输出即可

**美化代码**

上文中的一大段声明是以中文方式呈现，如果网站用的是多语言不就头疼了嘛，所以我们要遵循[Joomla!](http://www.Joomla178.com/)多语言功能设计，代码改为：

```php
<?php echo $this->item->text; ?><div class="link_notice"><?php echo JText::_('DIY_LINK'); ?>	<a href="/<?php echo $this->item->readmore_link; ?>">		<?php echo $this->item->title; ?>	</a></div>
```

解释一下就是通过内置方法JText::\_ 输出定义好的语言标识：DIY\_LINK，然后再到language/zh-CN/zh-CN.ini中最底添加翻译代码：

```html
DIY_LINK="原创文章，转载请保留本文链接："
```

最后，有的同学可能会考虑到用一个插件来实现，那么有了以上内容，做一个自己独用的插件也不是难事，在这里不单独说明，可先参考官方英文教学：[htteating\_a\_content\_plugin](http://docs.joomla.org/Creating_a_content_plugin)

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla!文章底部添加版权转载说明](http://www.joomla178.com/joomla-share/joomla-templates-tutorials/joomla-article-add-article-copy-right-bottom.html)
