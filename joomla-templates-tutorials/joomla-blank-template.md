---
title: "Joomla! 空白示例模板"
source: "http://www.joomla178.com/joomla-share/joomla-templates-tutorials/joomla-blank-template.html"
category: "JOOMLA模板开发"
author: ""
date: "2013-01-22"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla! 空白示例模板

如果你是使用joomla建站，而且喜欢自己写模板，但又想有css\js压缩等功能或者Bootstrap框架的空白模板，那么下面介绍的这款模板会很适合你。

文章来自：<http://www.ycway.com/joomla/joomla-25-and-30-blank-template.html>

### 一、关于blank.vc网站

这是空白模板的官方网站，地址是：[http://blank.vc](http://blank.vc/)，DBANK网盘下载：http://dl.vmall.com/c0khpl4sb9

- 你可以在官网免费下载该模板。
- 也可以浏览模板的快速使用指南和视频（比较简短）。
- 也可以付费购买他们的电子书教程，教程主要针对模板的使用开发还有模板集成的Modernizr、Twitter Bootstrap和PIE的使用，教程的费用大概1百多块人民币。

### 二、空白模板的优点

- 兼容joomla 2.5和joomla 3.0版本
- 干净，没有多余代码，适合用于模板开发
- css压缩功能，加快载入速度 （JS可减少http请求次数，但不进行代码压缩）
- 提供Modernizr  / PIE / Twitter Bootstrap 这三项可选的增强功能
- 适合开发多平台兼容的网站

### 三、空白模板的安装使用

### 1、到网站下载最新版本的空白模板。

到网站首页即可下载，得到的是模板安装包，可以直接安装使用；当然，一般情况下还是建议先进行修改订制成自己的安装包再进行安装，这样你开发多个网站的时候，就可以使用自己的空白模板安装包。

### 2、解压模板文件夹，修改文件。

#### 2.1 修改 templateDetails.xml 文件内容

```
<name>templatename</name><!--输入你的模板文件名--><creationDate>xxxx-xx-xx</creationDate><!-- 输入你的模板创建时间 --><author>your name</author><!-- 你的名字  --><copyright>Copyright © xxxx example.com</copyright><!-- 版权所属 --><authorEmail>your.name#example.com</authorEmail><!-- 你的电子邮箱地址#换成@  --><authorUrl>http://www.example.com</authorUrl><!-- 你的网站、博客地址 --><version>1.0.0</version><!-- 你的模板版本号 --><description><![CDATA[ <h1>你的模板名称</h1><p><img src="/../templates/templatename/template_preview.png" /></p><p>你可以插入一张图片，当然你也可以将其去掉</p><h3>Module positions</h3><ol><li>debug</li></ol><p>Created by <a href="http://www.example.com" target="_blank">your name | example.com</a>.</p>]]></description><!-- 按需要修改描述内容，可以使用html语言标签 --><languages folder="language"><!-- 中文用户可以按此修改 --><language tag="zh-CN">zh-CN.tpl_你的模板名称（当然你不要使用中文命名）.ini</language><language tag="en-GB">en-GB.tpl_templatename.ini</language></languages>
```

#### 2.2 修改语言文件 language/de-DE.tpl\_templatename.ini

更改为 language/zh-CN.tpl\_templatename.ini ，然后翻译其内容

```
TPL_TEMPLATENAME_PARAMETER_MODERNIZR_LABEL="Modernizr (14 KB)"TPL_TEMPLATENAME_PARAMETER_MODERNIZR_DESC="允许载入modernizr.js脚本文件"TPL_TEMPLATENAME_PARAMETER_MODERNIZR_DOC="<a href='http://modernizr.com/docs/' target='blank'>Modernizr 说明文档</a>"TPL_TEMPLATENAME_PARAMETER_BOOTSTRAP_LABEL="Twitter Bootstrap (211 KB)"TPL_TEMPLATENAME_PARAMETER_BOOTSTRAP_DESC="启用Twitter Bootstrap自适应模式"TPL_TEMPLATENAME_PARAMETER_BOOTSTRAP_DOC="<a href='http://twitter.github.com/bootstrap/scaffolding.html' target='blank'>Bootstrap说明文档</a>"TPL_TEMPLATENAME_PARAMETER_PIE_LABEL="PIE (41 KB)"TPL_TEMPLATENAME_PARAMETER_PIE_DESC="启用PIE (CSS3 for IE 8+7)"TPL_TEMPLATENAME_PARAMETER_PIE_DOC="<a href='http://css3pie.com/documentation/' target='blank'>PIE说明文档</a>"
```

#### 2.3 修改js/template.js.php文件

JS的一些参数设置部分，如果没有特别需要，建议保留默认的

增加需要用到的JS文件，使用语句：

```
require('你的JS文件名称');
```

前提是你已经把你的JS文件放置在模板的JS文件夹内

当然你不想载入默认的JS文件，可以将下面语句注释：

```
//require('../../../media/system/js/mootools-core.js'); //require('../../../media/system/js/core.js'); //require('../../../media/system/js/caption.js');
```

#### 2.4 修改 template.css.php 文件

增加需要用到的css文件，使用语句：

```
require('你的css文件名称');
```

前提是你已经把你的css文件放置在模板的css文件夹内

如果不需要用到默认的CSS文件，可以将其注释：

```
//require('../../../media/system/css/system.css');//require('../../system/css/system.css');//require('../../system/css/general.css');
```

template.css.php 和 template.js.php 文件的用法类似，一方面根据模板参数的设定动态加载相关的文件；一方面可以减少http请求次数，加快载入速度的作用

#### 2.5 修改index.php文件

如果你已经修改了template.js.php并注释了caption.js的载入语句，你就需要进行此修改，否则没必要做这步。

```
// unset scripts, put them into /js/template.js.php to minify http requestsunset($doc->_scripts[$this->baseurl.'/media/system/js/mootools-core.js']);unset($doc->_scripts[$this->baseurl.'/media/system/js/core.js']);unset($doc->_scripts[$this->baseurl.'/media/system/js/caption.js']);
```

在上面代码的后面添加

```
// Remove the JCaption code from within the template using a Regular Expressionif (isset($this->_script['text/javascript'])){$this->_script['text/javascript'] = preg_replace('%window\.addEvent\(\'load\',\s*function\(\)\s*{\s*new\s*JCaption\(\'img.caption\'\);\s*}\);\s*%', '', $this->_script['text/javascript']);if (empty($this->_script['text/javascript']))unset($this->_script['text/javascript']);}
```

用正则表达式移除代码

```
window.addEvent('load', function() {new JCaption('img.caption');});
```

若安装了k2，添加此代码：

```
unset($this->_scripts[$this->baseurl.'/media/system/js/modal.js']);unset($this->_scripts[$this->baseurl.'/media/k2/assets/js/k2.noconflict.js']);unset($this->_scripts[$this->baseurl.'/components/com_k2/js/k2.js']);unset($this->_styleSheets[$this->baseurl .'/media/system/css/modal.css']);
```

然后添加

```
if (isset($this->_script['text/javascript'])){$this->_script['text/javascript'] = preg_replace('%\s*window\.addEvent\(\'domready\',\s*function\(\)\s*{\s*SqueezeBox([\s\S]*)\s*var\s*K2SitePath\s*\=\s*\'([\s\S]*)\/\';\s*%', '', $this->_script['text/javascript']);$this->_script['text/javascript'] = preg_replace('%\s*window\.addEvent\(\'load\',\s*function\(\)\s*{\s*new\s*JCaption\(\'img.caption\'\);\s*}\);\s*%', '', $this->_script['text/javascript']);if (empty($this->_script['text/javascript']))unset($this->_script['text/javascript']);}
```

用正则表达式移除代码

```
<script type="text/javascript">window.addEvent('domready', function() {SqueezeBox.initialize({});SqueezeBox.assign($$('a.modal'), {parse: 'rel'});});var K2SitePath = '/peg2/';window.addEvent('load', function() {new JCaption('img.caption');});</script>
```

#### 2.6 修改以下文件的注释说明

- ndex.php
- component.php
- error.php
- offline.php
- html/modules.php
- js/template.js.php
- css/template.css.php

修改以上文件的关于版权说明的注释部分

#### 2.7 修改图片文件

- apple-touch-icon-57x57.png
- apple-touch-icon-72x72.png
- apple-touch-icon-114x114.png
- template\_thumbnail.png
- template\_preview.png

#### 2.8 修改网站小图标

favicon.ico

建议使用[在线生成网站图标](http://www.ycway.com/web-design/auto-generated-icon.html)。

#### 2.9 删除不需要用到的文件/文件夹

- psd
- CHANGELOG.txt
- README.md

### 四、将模板文件重新打包

如果你已经按自己的需求修改了相关的文件，这样就可以使用压缩工具重新打包成zip的安装包格式。

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla! 空白示例模板](http://www.joomla178.com/joomla-share/joomla-templates-tutorials/joomla-blank-template.html)
