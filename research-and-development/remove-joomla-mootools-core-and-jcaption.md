---
title: "移除Joomla的mootools-core.js和JCaption"
source: "http://www.joomla178.com/joomla-share/research-and-development/remove-joomla-mootools-core-and-jcaption.html"
category: "研究开发"
author: "Jiang"
date: "2013-08-22"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 移除Joomla的mootools-core.js和JCaption

![1b27709a4fbbcf05cd57c69289591981.png](../assets/16abf738de1771c46a23.png)

之前我们有研究过关于[Joomla! 3 删除原生JS框架](joomla3-remove-self-js.md)，在删除相关无用JS方面似乎还有更好的做法，下文内容转自[偶看博客](http://www.oukan.net/2013061328.html)

偶看在使用Joomla 3.1建站的时候发现，Joomla会在网页head区域自动添加mootools-core.js等JS文件，还会添加JCaption，完整的代码为

```
<script src="/media/system/js/mootools-core.js" type="text/javascript"></script><script src="/media/system/js/core.js" type="text/javascript"></script><script src="/media/system/js/caption.js" type="text/javascript"></script><script type="text/javascript">window.addEvent('load', function() {	new JCaption('img.caption');});</script>
```

对于偶看来说，这些代码都用不上，而且这些代码体积还不算小，通过查看“Mootools Enabler/Disabler”插件的源代码，偶看找到了去除JS的核心代码，将以下代码添加到模板文件夹下的 index.php 的头部

```
<?php        $app = JFactory::getApplication();        $doc = JFactory::getDocument();        $pageParams = $app->getParams();        unset($doc->_scripts[JURI::root(true) . '/media/system/js/mootools-core.js']);        unset($doc->_scripts[JURI::root(true) . '/media/system/js/mootools-more.js']);        unset($doc->_scripts[JURI::root(true) . '/media/system/js/core.js']);        unset($doc->_scripts[JURI::root(true) . '/media/system/js/caption.js']);        unset($doc->_scripts[JURI::root(true) . '/media/system/js/modal.js']);        unset($doc->_scripts[JURI::root(true) . '/media/system/js/mootools.js']);        unset($doc->_scripts[JURI::root(true) . '/plugins/system/mtupgrade/mootools.js']);?>
```

删除了JS文件还不够，还需要删除head代码，否则，浏览器会报错。

```
window.addEvent('load', function() {	new JCaption('img.caption');});
```

删除以上代码的解决方案来自：[Removing JCaption in Joomla!2.5](http://www.acuit.com.au/Blogs/removing-jcaption-in-joomla2.5.html)，对于Joomla 3.1也是同样适用的。

还是在模板文件夹下的 index.php 的头部，添加正则表达式

```
if (isset($this->_script['text/javascript'])){    $this->_script['text/javascript'] = preg_replace('%window\.addEvent\(\'load\',\s*function\(\)\s*{\s*new\s*JCaption\(\'img.caption\'\);\s*}\);\s*%', '', $this->_script['text/javascript']);    if (empty($this->_script['text/javascript']))        unset($this->_script['text/javascript']);}
```

即可将JCaption代码删除，那么最后完整版本为：

```
<?php        $app = JFactory::getApplication();        $doc = JFactory::getDocument();        $pageParams = $app->getParams();        unset($doc->_scripts[JURI::root(true) . '/media/system/js/mootools-core.js']);        unset($doc->_scripts[JURI::root(true) . '/media/system/js/mootools-more.js']);        unset($doc->_scripts[JURI::root(true) . '/media/system/js/core.js']);        unset($doc->_scripts[JURI::root(true) . '/media/system/js/caption.js']);        unset($doc->_scripts[JURI::root(true) . '/media/system/js/modal.js']);        unset($doc->_scripts[JURI::root(true) . '/media/system/js/mootools.js']);        unset($doc->_scripts[JURI::root(true) . '/plugins/system/mtupgrade/mootools.js']);if (isset($this->_script['text/javascript'])){    $this->_script['text/javascript'] = preg_replace('%window\.addEvent\(\'load\',\s*function\(\)\s*{\s*new\s*JCaption\(\'img.caption\'\);\s*}\);\s*%', '', $this->_script['text/javascript']);    if (empty($this->_script['text/javascript']))        unset($this->_script['text/javascript']);}?>
```

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [移除Joomla的mootools-core.js和JCaption](http://www.joomla178.com/joomla-share/research-and-development/remove-joomla-mootools-core-and-jcaption.html)
