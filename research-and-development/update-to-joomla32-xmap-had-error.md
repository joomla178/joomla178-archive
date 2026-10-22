---
title: "升级到Joomla! 3.2后 Xmap报错无法显示"
source: "http://www.joomla178.com/joomla-share/research-and-development/update-to-joomla32-xmap-had-error.html"
category: "研究开发"
author: "Jiang"
date: "2013-11-11"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 升级到Joomla! 3.2后 Xmap报错无法显示

在升级到Joomla! 3.2 之后，网站地图插件Xmap无效，并表现为空白，如果php设置的是显示php报错，那么我们能看到下述错误提示：

```
Warning: require_once(/home/xxx/xxx.../includes/application.php) [function.require-once]: failed to open stream: No such file or directory in /home/xxx/xxx.../components/com_xmap/helpers/xmap.php on line 12
```

出现这个问题其实很明显告诉了我们问题所在，需要的组件文件丢失问题，在/components/com\_xmap/helpers/xmap.php文件中代码第12行报错，打开此文件，修改下述代码：

```
require_once(JPATH_SITE .'/includes/application.php');
```

修改为

```
require_once(JPATH_SITE .'/libraries/cms/application/site.php');
```

相信不久后，Xmap的新版中会解决此BUG

不过由此可见，Joomla! 3.2在库文件的处理上做了不小的调整！

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [升级到Joomla! 3.2后 Xmap报错无法显示](http://www.joomla178.com/joomla-share/research-and-development/update-to-joomla32-xmap-had-error.html)
