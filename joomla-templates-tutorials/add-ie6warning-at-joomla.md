---
title: "如何在Joomla!中增加IE6升级提醒"
source: "http://www.joomla178.com/joomla-share/joomla-templates-tutorials/add-ie6warning-at-joomla.html"
category: "JOOMLA模板开发"
author: ""
date: "2013-07-11"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 如何在Joomla!中增加IE6升级提醒

早先由本站翻译的一款IE提示升级插件还是挺好用的：[IEWarning v2.5 for Joomla1.7 简体中文版【Joomla178版】](http://www.Joomla178.com/joomla-extensions/joomla-plugins/441-iewarning-v25-for-joomla17-simple-chinese.html)但是在每个模板中的表现可能也会有一些问题，今天就给大家说一说如何DIY这样的提醒升级IE6的功能。

![ie6-warning-diy.png](../assets/6788ef1806427b938cfd.png)

做这样一个提醒，我们主要用到jquery，大致思路就是做一个全屏遮罩层，然后在这个遮罩层的上面把提醒升级的代码做上去。

### 第一步，在模板中引入jQuery库

此前我们在很多文章中提过修改模板文件，比如1.5时代的[Joomla模板制作实战教程【一】-创建一个简单的模板](joomla-templates-tutorials-creat-a-simple-template.md)，在Joomla! 2.5中我们讨论过如何DIY文章、分类的[Joomla! 2.5.x 文章布局、分类布局模板释疑](joomla25-article-layout-and-blog-layout.md)。其中都说明了模板文件的修改方法

打开/templates/jk\_Joomla178/index.php文件，找到代码：

```
<jdoc:include type="head" />
```

<jdoc:include type="head" />主要是Joomla! 引用所有原生框架资源的语句，最好在其前面或者后面增加代码如下：

```
<jdoc:include type="head" /><script type="text/javascript" src="http://www.Joomla178.com/templates/jk_Joomla178/js/jquery.min.js"></script>
```

记得将jquery库放在你的模板目录中，这里只是用Joomla178.com为实例演示

### 第二步，制作浏览器升级警告弹框

首先主体部分的html代码，大致意思是标题警告，然后提供多个浏览器的最新版本下载地址，在</body>上面加入以下代码，并附上ie6的条件句（<!--[if lte IE 6]>...<![endif]-->），当然这里你还可以写成ie7及ie7以下就条件成立：

```
<!--[if lte IE 6]><div class="ie6warning"><h1>IE6浏览器该从地球上消失了</h1><p>您正在使用 Internet Explorer 6 浏览网页，如果您升级到 Internet Explorer 8，或者 Internet Explorer 9（需操作系统支持），当然我们更推荐您转换到其它安全浏览器，不但可以获得更好的网站浏览体验，而且您的上网会变的更安全，请参考以下浏览器升级标准。</p><ul class="clearfix"><li class="up_ie"><a href="http://www.microsoft.com/windows/Internet-explorer/default.aspx" target="_blank"><span>IE8</span></a></li><li class="up_chrome"><a href="http://www.google.com/chrome" target="_blank"><span>Chrome 2.0+</span></a></li><li class="up_firefox"><a href="http://www.mozilla.com/firefox/" target="_blank"><span>Firefox 3+</span></a></li><li class="up_opera"><a href="http://www.opera.com/download/" target="_blank"><span>Opera 9.5+</span></a></li><li class="up_safari"><a href="http://www.apple.com/safari/download/" target="_blank"><span>Safari 3+</span></a></li></ul><p><a href="javascript:" id="goon">我想继续浏览</a></p></div><div id="wwrap" style="position:absolute; top:0; left:0; background-color:rgba(14,16,9,0.8); background:#100e09\9; filter:alpha(opacity=80)\9;z-index:100002;"></div><![endif]--></body>
```

解释一下代码，主要是由class为ie6warning的标签和全屏遮罩层的id为wwrap标签组成，遮罩层的宽高由马上写的js来读全屏宽高，另外通过z-index:100002;这个样式来控制整个弹层的层级，尽量让这个值更大，避免其它弹框在其上面。

然后我们要给上述代码增加css样式，这样保证他们看起来更好看，在<jdoc:include type="head" />下方或者</head>之前增加代码如下：

```
<jdoc:include type="head" /><!--[if lte IE 6]><style>.ie6warning{ position:absolute;left:50%; top:200px; width:660px; padding:20px; margin-left:-350px; background:#fff; color:red; border:1px solid #000; z-index:200000;}.ie6warning h1{ font-size:18px; margin-bottom:20px;}.ie6warning p{ margin:10px 0;}.ie6warning ul li{ display:inline-block; margin-right:10px; float:left; background:url(../images/background_browser.gif) no-repeat center top;}.ie6warning ul li a{ display:inline-block; width:120px; height:22px; padding-top:100px; text-align:center;}.ie6warning ul li.up_ie a{ background:url(../images/browser_ie.gif) no-repeat center top;}.ie6warning ul li.up_chrome a{ background:url(../images/browser_chrome.gif) no-repeat center top;}.ie6warning ul li.up_firefox a{ background:url(../images/browser_firefox.gif) no-repeat center top;}.ie6warning ul li.up_opera a{ background:url(../images/browser_opera.gif) no-repeat center top;}.ie6warning ul li.up_safari a{ background:url(../images/browser_safari.gif) no-repeat center top;}.ie6warning ul li a span{}	</style><![endif]--> 
```

上述代码的css中有引用各浏览器图标需要自行准备放入/templates/jk\_Joomla178/images/ 目录下

最后，我们需要写入JS方法，让IE6用户一进来页面就迎来的是警告弹框，在<jdoc:include type="head" />下方增加JS代码如下，在这里我们公用了ie6的条件句，所以就和样式代码合并：

```
<jdoc:include type="head" /><!--[if lte IE 6]><script>$(document).ready(function(){	var scrW=$(window).width(), scrH=document.documentElement.scrollHeight;	$("#wwrap").css('height',scrH+260);	$("#wwrap").css('width',scrW);	$("#goon").click(function(e) {        $("#wwrap, .ie6warning").hide();    });	})</script><style>.ie6warning{ position:absolute;left:50%; top:200px; width:660px; padding:20px; margin-left:-350px; background:#fff; color:red; border:1px solid #000; z-index:200000;}.ie6warning h1{ font-size:18px; margin-bottom:20px;}.ie6warning p{ margin:10px 0;}.ie6warning ul li{ display:inline-block; margin-right:10px; float:left; background:url(../images/background_browser.gif) no-repeat center top;}.ie6warning ul li a{ display:inline-block; width:120px; height:22px; padding-top:100px; text-align:center;}.ie6warning ul li.up_ie a{ background:url(../images/browser_ie.gif) no-repeat center top;}.ie6warning ul li.up_chrome a{ background:url(../images/browser_chrome.gif) no-repeat center top;}.ie6warning ul li.up_firefox a{ background:url(../images/browser_firefox.gif) no-repeat center top;}.ie6warning ul li.up_opera a{ background:url(../images/browser_opera.gif) no-repeat center top;}.ie6warning ul li.up_safari a{ background:url(../images/browser_safari.gif) no-repeat center top;}.ie6warning ul li a span{}	</style><![endif]--> 
```

解释一下其中的JS方法，分别定义了一个浏览器宽度和一个页面高度的变量，然后将其通过jquery的css方法赋值给id为wwrap的遮罩层，当点击id为goon（继续浏览的意思）标签，整套弹层隐藏即可。

这样下来，我们整个IE浏览器升级警告的DIY就算完成了，虽然没有插件那样完美，不过做起来还是很方便，当然有兴趣的同学可以将其制作为Joomla!版插件，此方法适用于Joomla! 各版本

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [如何在Joomla!中增加IE6升级提醒](http://www.joomla178.com/joomla-share/joomla-templates-tutorials/add-ie6warning-at-joomla.html)
