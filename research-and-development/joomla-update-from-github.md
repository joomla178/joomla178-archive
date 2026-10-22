---
title: "Joomla!转到GitHub后无法后台更新解决办法"
source: "http://www.joomla178.com/joomla-share/research-and-development/joomla-update-from-github.html"
category: "研究开发"
author: "Jiang"
date: "2014-10-28"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla!转到GitHub后无法后台更新解决办法

好久不见，前后因为身体上的原因，再加上家里面的一些事好几个月没更新，也没时间翻译官方版本更新，最近登录后台发现已经无法一键更新Joomla!的补丁了，虽然后台显示为github的域名地址，但是好像经过了cdn分发之后，下载补丁的地址成了amazon的地址，后台更新便无解。

那么解决办法就是到Joomla!在Github的项目上去直接下载，地址是：<https://github.com/joomla/joomla-cms/tags>

登录到这个地址之后，选择最近的3.3.6版本，地址是<https://github.com/joomla/joomla-cms/releases/tag/3.3.6>

比如我当前的后台是3.3.3，那么必然选择**Joomla\_3.3.x\_to\_3.3.6-Stable-Patch\_Package.zip** 这个进行下载，其实这个地址也是amazon的，但是下载还是蛮顺利，下载完成之后上传到网站目录  /tmp/ 下，如果是阿里云，记得改zip的权限、用户组。

这时候再到Joomla后台进行一键更新，就过了！！

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla!转到GitHub后无法后台更新解决办法](http://www.joomla178.com/joomla-share/research-and-development/joomla-update-from-github.html)
