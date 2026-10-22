---
title: "Joomla!升级至Joomla! 2.5的常见错误解决办法"
source: "http://www.joomla178.com/joomla-share/research-and-development/joomla-upgrade-joomla25-error-resolve.html"
category: "研究开发"
author: "Jiang"
date: "2013-01-09"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla!升级至Joomla! 2.5的常见错误解决办法

![Be careful upgrading to joomla 2.5](../assets/8302a218c3f0007e7bff.jpg)

[Joomla!](http://www.Joomla178.com/) 2.5 作为长期支持版本，升级肯定是有非常有必要的，不仅仅表现在新功能上，还需要注意的是一些过往BUG，因[Joomla!](http://www.Joomla178.com/) 2.5推出了[一键升级](joomla17-update-to-joomla25.md)功能，详细[一键升级](joomla17-update-to-joomla25.md)请参阅：[Joomla 1.7升级至2.5，1.7模板可直接使用](joomla17-update-to-joomla25.md)。当然升级自然会遇到各种古怪问题，下文内容译自[Upgrading to Joomla 2.5 - SomeWarnings](http://brian.teeman.net/joomla/774-upgrading-to-joomla-2-5-some-warnings)，总结了一些常见问题的解决方案。

### 清除缓存

[Joomla!](http://www.Joomla178.com/) 2.5对JS库、CSS库有了新的更新，这些都会对前台、后台的原有效果有所影响，当然也有可能发生不可预知的问题。 如果出现一些后台功能无法工作情况，那就需要清除一下浏览器缓存和Joomla的缓存，关于Joomla的缓存在[让Joomla网站继续飞](http://www.Joomla178.com/joomla-share/research-and-development/294-let-joomla-fast.html)一文中详细提及。

### 数据库修复

[一键升级](joomla17-update-to-joomla25.md)并不支持一部分数据库的更新，不过不用担心，[Joomla!](http://www.Joomla178.com/) 2.5.高明之处正在于此，升级之后要在“扩展管理”-“数据库”中点击“修复”即可！（这是在[Joomla!](http://www.Joomla178.com/) 2.5.x中的新功能，[Joomla!](http://www.Joomla178.com/) 1.7.x是看不到的哦）。

### 新插件、新模块

[一键升级](joomla17-update-to-joomla25.md)后当然会有一些插件、模块失效，通常数据库修复是可以解决这类问题，不过最好还是将插件、模块更新一下，进入“扩展管理”-“更新”进行更新，发现更新之前需要点击右上角“清除缓存”，如果这个时候下方列表出现了更新文件，勾选即可进行更新。

需要注意的是，如果扩展已经安装好最新版、或者不可用，那么“更新”是无效的哦。

### HTML文本筛选

文本过滤已经从文章管理转移到全局设置中了，所以要再次确认一下之前的文本过滤是否仍然有效，另外也是非常重要的一点，无论如何都要在全局设置中再保存一次文本过滤设置，这个自然是有用的，编者话：我们大多数情况下都在用JCE或者其它功能更强大的编辑器，所以这个文本过滤不太经常用到。

### 前端JS

在过去的版本中，我们大多数情况下选择禁用了前端的Mootools库，因为在新的版本中captions.js 发生了变化，如果前端不加载Mootools的JS库的话，前端可能会废掉了，同样后台也会因此导致复选框、弹框失效，这个真的要清除浏览器缓存、cookies之类！比如Chrome浏览器是真要清！

### 我的网站正在使用[Joomla!](http://www.Joomla178.com/)的什么版本?

最后一段话我想告诉大家的是，[Joomla!](http://www.Joomla178.com/)的版本可以在后台很直观的看到，也建议中文朋友们不要再试图去掉[Joomla!](http://www.Joomla178.com/) 的开源提示了，大胆地告诉您的客户或者老板，这就是强大的[Joomla!](http://www.Joomla178.com/) 任何程序都有漏洞，不代表开源就是漏洞更多，要知道这是世界级的顶级程序员们做出来的程序，他们一直在努力完善。

文中部分译文与原文不符，敬请谅解

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla!升级至Joomla! 2.5的常见错误解决办法](http://www.joomla178.com/joomla-share/research-and-development/joomla-upgrade-joomla25-error-resolve.html)
