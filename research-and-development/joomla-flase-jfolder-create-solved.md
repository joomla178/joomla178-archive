---
title: "Joomla!常见问题之JFolder::create: 解决办法"
source: "http://www.joomla178.com/joomla-share/research-and-development/joomla-flase-jfolder-create-solved.html"
category: "研究开发"
author: "Jiang"
date: "2013-03-18"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla!常见问题之JFolder::create: 解决办法

一个老问题，大家可能也会经常遇上，不管你是在安装扩展或者更新什么的时候，要是出现JFolder::create: 错误该怎么解决呢？

老问题，在过去的因为安装某个扩展会出现这种情况，比如“JFolder::create: Could not create directory”，自从[Joomla! 2.5开始有了在线更新](joomla17-update-to-joomla25.md "Joomla 1.7升级至2.5，1.7模板可直接使用")的时候也可能会出现这种问题，其实问题很简单，我们只要找到出问题的原因，就不再纠结什么新问题了。

出现这个问题，一般是在网站迁移之后，特别是[手动迁移Joomla!整站](joomla-backup-all-step.md)，主要问题是出现在logs和tmp两个文件夹，要么是权限问题，要么是路径不对，一般本地windows环境的话只要把logs,tmp文件夹重新定位一下即可，Linux的环境中就有可能是logs,tmp路径或者权限可能有问题。解决办法简单：

1. 想办法找到网站目录下修改configuration.php文件
2. 查找$log\_path和$tmp\_path，会发现以下代码（示例是本地windows下的wamp环境）：

   ```
   //Joomla!2.5.x格式：public $log_path = 'E:/wamp/www/joomla/logs';public $tmp_path = 'E:/wamp/www/joomla/tmp';//Joomla!1.5.x格式：var $log_path = 'E:/wamp/www/joomla/logs';var $tmp_path = 'E:/wamp/www/joomla/tmp';
   ```
3. 修改$log\_path和$tmp\_path后面的值分别为'./logs'和'./tmp'就可以了，保存文件即可搞定

当然一些其它的症状也有可能并不是如此解决，比如在扩展作者的在线更新服务器故障也会有可能。

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla!常见问题之JFolder::create: 解决办法](http://www.joomla178.com/joomla-share/research-and-development/joomla-flase-jfolder-create-solved.html)
