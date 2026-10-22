---
title: "修改Joomla文章标题的语义化标签"
source: "http://www.joomla178.com/joomla-share/research-and-development/modify-joomla-article-title-code.html"
category: "研究开发"
author: "Jiang"
date: "2013-03-10"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 修改Joomla文章标题的语义化标签

Multithumb found errors on this page:  
  
There was a problem loading image http://www.joomlagate.com/images/stories/article/joomla25-tutorials/heading-tags.jpg  
There was a problem loading image http://www.joomlagate.com/images/stories/downloads/2013downloads/header-tags-plugin-parameters.png

笔者记：该文也可以参考[Joomla! 2.5.x 文章布局、分类布局模板释疑](../joomla-templates-tutorials/joomla25-article-layout-and-blog-layout.md)中有详细介绍

从搜索引擎优化（SEO）的角度看，网页上被 H1 标记包绕的内容是最重要的关键词。但遗憾的是，Joomla 2.5的开发人员显然没有理解这一点：他们在Joomla! CMS核心源文件中置入代码，使得文章标题默认使用 H2 标记。这个 H2 标记等于告诉搜索引擎：这个内容（文章标题）不是最重要的。无疑这样会降低文章标题的 SEO 权重。如果网站上文章数量很多，那么最终结果就降低了整个网站的SEO排名。我刚刚检查了目前最新的Joomla 2.5.9 核心，糟糕的是这个问题依然存在。由于“给文章标题赋予 H2 标记”这一点是直接写在核心源文件中的，所以更改起来也不太容易。本文介绍一下如何轻松将文章标题的 H2 标记改为 H1 标记，从而重新得到本应属于 Joomla 文章标题的 SEO 权重。

![heading-tags.jpg](http://www.joomlagate.com/images/stories/article/joomla25-tutorials/heading-tags.jpg)

首先我们来看一下，Joomla 核心的那些代码导致了这个问题：

打开 /components/com\_content/views/article/tmpl/default.php 这个文件，在第36行至43行，可以看到如下代码：

```
<h2>
<?php if ($params->get('link_titles') && !empty($this->item->readmore_link)) : ?>
    <a href="/<?php echo $this->item->readmore_link; ?>">
    <?php echo $this->escape($this->item->title); ?></a>
<?php else : ?>
    <?php echo $this->escape($this->item->title); ?>
<?php endif; ?>
</h2>
```

这段代码就是导致 Joomla! 文章标题被默认使用 H2 标记的来源。我们的解决办法也就相应产生了：

### 第一种方法：直接修改核心代码

如果将上述核心代码中的 H2 修改为 H1，这个问题就解决了。这种方法虽然快捷，但是带来了一个不可忽视的新问题：下次升级 Joomla 核心时，此文件有可能被新版本覆盖，从而使这种修改（hacking）失效。

难道把这个方案记录下来，每次升级完核心都再重新修改一次源文件？当然不行，这样太辛苦了。如果你管理好几个网站，而且有好几个文件都要修改，哪能忙得过来？所以，这个方法只做一种参考，不推荐使用。

### 第二种方法：利用“HTML 输出僭越”（HTML overriding）

HTML Overriding 这个方法在 Joomla! 1.5 时代就有了，当时 Joomla之门 网站撰文介绍时称之为“优先输出”，现在我觉得“僭越”这个中文词汇比“优先输出”翻译 Override 一词更确切。

具体方法（假设你目前使用的模板名称为 your\_template\_name）：

1. 将刚才提到的 /components/com\_content/views/article/tmpl/default.php 文件复制为 /templates/your\_template\_name/html/com\_content/article/default.php （某些商业模板已经做过这一步，那么可以跳过）；
2. 打开 /templates/your\_template\_name/html/com\_content/article/default.php 这个新文件，找到刚才所说的 H2 标记，改为 H1，保存、上传；

这就 OK 了。由于这个方法没有变动 Joomla CMS 核心文件，因此你以后再怎么升级网站核心，都不会影响这个修改结果。

### 第三种方法：安装第三方插件自动修改 H2 标记为 H1

上面提到的第二种方法，在不太熟悉 PHP 编程的普通用户看来，还是有点胆怯。别吃惊，确实有一部分人一提到“修改代码”就有点不舒服。那么，我们可以通过安装一个 Joomla 扩展，来轻松更改文章标题的 H2 标记为 H1。

如果你网站使用了某种高级 SEF 组件，例如 sh404SEF（收费软件），你会在它的 SEO 设置参数中找到一项“给文章标题使用 H1 标记”的选项。启用此功能就解决了这个问题。

不过，或许你网站选择了其它 SEF 组件，或者，你认为单单为了改动一个文章标题的 heading 标记，没必要“牛刀杀鸡”，那么我们介绍一个专门处理 heading 标记的小插件：Header Tags。

![Heager Tags 插件的参数](http://www.joomlagate.com/images/stories/downloads/2013downloads/header-tags-plugin-parameters.png)

安装了 Heager Tags 插件之后，在“基本选项”那里将内容区域选择为“组件输出”，然后在“控制 H1 标记”这里，按照上图设置（实际上这也是默认设置）。然后启用该插件并保存参数。现在查看前台文章页面，文章标题已经由 H2 标记变成 H1 了。

### 注意模板默认将网站 Logo 设为 H1 的情况

刚才我们设置 Header Tags 插件的时候，内容区域选择的是“组件输出”，也就是说，只在模板上的 component 区域查找、替换 heading 标记，并不涉及网页的其它部分。这就要注意一点：某些模板已经默认将网站 Logo（不管是图片格式还是文字格式）设置使用 H1 标记。由于 Logo 通常在站内每一个页面上都显示，那么，在这种情况下如果启用了 Header Tags 插件并按照上述方法设置，就会造成同一个页面上存在两个 H1 标记：一个属于网站 Logo，一个属于文章标题。这显然也不利于 SEO，因为这让搜索引擎很为难，搞不懂到底哪个 H1 是最重要的？

一旦发现这种情况（在安装 Header Tags 插件之前通过查看页面源代码就能找到现有的 H1 标记属于哪个内容），就必须修改模板文件了。由于网站的模板并不经常更换、升级，所以可以放心修改模板的源文件。为了备忘，可以在网站维护记录里面登记这一操作，同时将修改的文件保存一份原版备份（文件扩展名添加 .bak 后缀）。修改方法也很简单，就是直接去掉给 Logo 的 H1 标记，不给 Logo 使用任何 heading 标记。

文章来自：http://www.joomlagate.com/article/joomla25-tutorials/how-to-change-h2-tag-to-h1-tag-in-the-articles-title-in-joomla/

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [修改Joomla文章标题的语义化标签](http://www.joomla178.com/joomla-share/research-and-development/modify-joomla-article-title-code.html)
