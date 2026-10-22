---
title: "Joomla 2.5 + Ucenter(discuz)整合同步登录的插件"
source: "http://www.joomla178.com/joomla-share/research-and-development/joomla25-and-ucenter-users.html"
category: "研究开发"
author: "Jiang"
date: "2012-08-18"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla 2.5 + Ucenter(discuz)整合同步登录的插件

Multithumb found errors on this page:  
  
There was a problem loading image http://admclub.com/wp-content/uploads/2012/01/uc-auth.jpg  
There was a problem loading image http://admclub.com/wp-content/uploads/2012/01/juc-1.png  
There was a problem loading image http://admclub.com/wp-content/uploads/2012/01/juc-2.png  
There was a problem loading image http://admclub.com/wp-content/uploads/2012/01/uc-all.jpg

**原创插件，转载请注名出处：[http://admclub.com](http://admclub.com "admclub.com")**  
 支持Joomla 1.7/2.5,UCenter 1.6.

~~注：Joomla 2.5.4后，因为对原来核心组件模块锁定了，不能从后台替换核心模块/插件。此问题正在解决中。~~  
 解决方法：  
 使用phpMyAdmin打开表： #前缀\_extensions，然后找到name的值为plg\_authentication\_joomla的插件，然后修改这条记录。把protected均设值为0。

实现功能:

1.当从Joomla登录时,如果UCenter用户存在,则使用UCenter上的用户信息校验密码.则否使用Joomla本地信息.同步更新,删除Joomla和UCenter用户.

2.可选只使用UCenter用户信息,而不理会Joomla本地用户信息.

3.可选同步登录,删除,更新用户时,是否先检查用户是否存在重得,如果重得,则不作同步.

4.组件后台提供用户复制功能.按UCenter官方手册建议,使用前最好先将Joomla用户复制到UCenter.并需要处理好用户重名的问题.如果你的Joomla是新的,没有任何用户,可以不复制用户.如果你的系统存在除UCenter和Joomla之外的其它应用,建议纳UC官方的建议.否则可能出现权限提升的问题.

具个例子,某用户A在Joomla中是管理员,而之前并没在UC中.且在您的系统合并后,用户A一直没有登录过,就是说这个用户A一直没有被同步到UC中,而后来用户B却跑到你的第三方应用,如DZ X2注册了与用户A同名用户.那么当这个假的用户A从X2登录后,也能同步登录到Joomla中,原来的用户A,就无法再正常登录了.按UC官方的建议,事先将用户复制到UC的话,就可以很好地解决这个安全问题.

我发现其它同类插件很少提及到这点.

5.安装即用,不修改Joomla原来代码.

安装使用方法:

1.复制api和uc\_client目录到Joomla安装根目录  
 2.然后安装并正确然后配置UCenter组件.  
 3.安装并激活System - ucenter插件,  
 4.安装并激活User - ucenter插件,由于本组件不具有其它的用户管理管理功能，**请保留其它用户插件的状态**,  
 5.安装并激活Authentication - ucenter 插件,然后停用**Authentication - Joomla**插件,否则会有冲突.  
 [![uc-auth](http://admclub.com/wp-content/uploads/2012/01/uc-auth.jpg "uc-auth")](http://admclub.com/wp-content/uploads/2012/01/uc-auth.jpg)  
 6.防止因用户名相同的情况而引起权限提升的问题,  
 请首先将Joomla用户复制到UCenter. 如果出现重复的用户(在Joomla和UCenter都存在的同名用户),会被记录在uc\_mergemembers表(uc\_为UCenter表前缀) 中.您需要手工对这些用户进行检验,当确定用户有效性后,您可以使用第三方工具(如phpmyadmin)将此用户从uc\_mergemembers表中 删除.  
 **注意:所有有重复问题的用户,都不能被同步登录、同步更新，删除.但如果此用户从Joomla,且本地密码与UCenter密码相同,本模块会认为此用户合法,当首次从Joomla登录后,自动将此用户从mergemembers表中删除.**

后台截图:

后台主页面:

[![juc-1](http://admclub.com/wp-content/uploads/2012/01/juc-1.png "juc-1")](http://admclub.com/wp-content/uploads/2012/01/juc-1.png)

配置界面:

[![juc-2](http://admclub.com/wp-content/uploads/2012/01/juc-2.png "juc-2")](http://admclub.com/wp-content/uploads/2012/01/juc-2.png)

所有相关插件：

[![uc-all](http://admclub.com/wp-content/uploads/2012/01/uc-all.jpg "uc-all")](http://admclub.com/wp-content/uploads/2012/01/uc-all.jpg)

~~晕,忘了上传了~~

=======================2012.04.21更新 ==========================

先不上传了，需要测试版的朋友EMAIL吧。

周末，花了点时间搭了个DEMO环境，

Joomla 2.5.4:[http://ju.admclub.com](http://ju.admclub.com "Joomla+Discuz整合演示")  
 *(原本想把Joomla和Uenter放在同一域名的，后来觉得分开两个子域名更能体现出特性。)*

Discuz X2.5: [http://dz.admclub.com](http://dz.admclub.com "Joomla+Discuz整合演示")

已知BUG:

DZ中文名无法登入JOOMLA，显示找不到该页 20120528 感谢小猪

文章来自：[Joomla+Ucenter(discuz)整合同步登录的插件](http://admclub.com/view/joomla-ucenter-discuz-share-user-component)

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla 2.5 + Ucenter(discuz)整合同步登录的插件](http://www.joomla178.com/joomla-share/research-and-development/joomla25-and-ucenter-users.html)
