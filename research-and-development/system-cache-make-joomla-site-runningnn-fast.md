---
title: "System-cache让Joomla网站速度再翻倍,像子弹在飞"
source: "http://www.joomla178.com/joomla-share/research-and-development/system-cache-make-joomla-site-runningnn-fast.html"
category: "研究开发"
author: "Jiang"
date: "2011-02-14"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# System-cache让Joomla网站速度再翻倍,像子弹在飞

之前有讲过一篇[合理利用joomla cache(缓存) 让网站速度翻倍](77.md) 使得Joomla建的网站，从某些程序上让网站速度得到提升，但这离大家所爱好的“静态生成”还相差甚远。**（原创文章转载请标明出处，请引用本文地址）**

在Unforgivable的指点下，发现在system-cache这个让我们不曾注意的东西，通常我们只是利用了全局配置中的cache，开启了之后并未感到有质的飞越，下面就说说这个system-cache。

**如何利用**

1、首先肯定是要开启全局配置中的cache，参照[合理利用joomla cache(缓存) 让网站速度翻倍](77.md)，配置一个适中的缓存时间

2、第二步前往**扩展->插件->System-cache**，启用并配置一个合适的系统缓存时间（视网站更新频率而定，原理同上篇文）。很简单，保存，**并即时清空缓存！再必须清空本地浏览器的记录，以比较首次载入速度。**

**负面影响**

开启System-cache会带来一些负面影响，诸如“会员登陆”、“投票”等需提交的组件、模块无法生效，而且会出现不同的BUG（这时候的system-cache开启就类似静态生成，已经生成了大量的html文件），另外值得一提的是，当开启了**SEF友好网址**后，有些图片的路径识别会发生改变，产生了图片无法显示的结果。

**另外开启System-cache之后，将会生成大量的缓存文件，请注意增加空间主机的容量，并及时按周期清理缓存**

**解决办法**

1、关于提交类扩展无法运作，可使用一款名为[JotCache](http://extensions.joomla.org/extensions/site-management/cache/13155)的插件实现，大致原理就是选择性的生成缓存，让user、polls这些组件不缓存，关于使用方法，将单独成文细述。

2、关于开启SEF友好网址后，图片路径的改变。首先前往\libraries\joomla\document\html\renderer\head.php中修改（请注意备份，该文件为核心文件）

找到代码66行

```
$strHtml .= $tab.'<base href="'.$document->getBase().'" />'.$lnEnd;
```

将代码改为：

```
$strHtml .= $tab.'<base href="'.JURI::base().'" />'.$lnEnd;
```

找到模板文件，视各模板而定，通常情况下是文件\templates\jk\_Joomla178\index.php （将模板名jk\_Joomla178替换成你的模板）

找到代码：

</head>

**在其前面添加代码:**

<base href="http://www.Joomla178.com/" />

将href中的http://www.Joomla178.com/ 替换成你的网站，如http://www.youname.com/

**最后还要强调一点，注意备份修改的核心文件，末了添加文章、投票、联系等新内容后，要执行一次缓存清理，前台才会出现新添的项目内容**

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [System-cache让Joomla网站速度再翻倍,像子弹在飞](http://www.joomla178.com/joomla-share/research-and-development/system-cache-make-joomla-site-runningnn-fast.html)
