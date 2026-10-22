---
title: "Joomla!网站迁移备份全过程"
source: "http://www.joomla178.com/joomla-share/research-and-development/joomla-backup-all-step.html"
category: "研究开发"
author: "Jiang"
date: "2012-12-29"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla!网站迁移备份全过程

很多同学在本地做好了网站之后上传到服务器上总会遇上各种问题，所以有许多人选择使用了[Joomla!](http://www.Joomla178.com/) 下的各种备份扩展，其实手工迁移备份也是很方便的，有两种方法：第一种在『[教你如何创建joomla的quickstart安装包](http://www.Joomla178.com/joomla-share/research-and-development/316-how-to-create-a-quickstart-package-joomla.html)』中可以查阅，第二种就是纯手工迁移之用分四步，备份迁移程序文件，备份数据库，迁移数据库，修改配置文件，本文对第二种方法详解：

### 第一步，备份迁移程序文件

在Windows服务器中（或者本地服务器如wamp,xampp等）找到网站所在目录，将所有文件档案压缩成zip压缩包即可完成程序文件的备份，在Linux服务器、虚拟主机、VPS）中都有针对网站目录的压缩功能，如果服务器中没有提供压缩功能，大家还可以通过php程序压缩，详情请参阅『[让国内PHP主机支持在线解压解决方法](138.md)』一文。解压之后等待下面两步之后在第四步查看修改数据库配置文件configraution.php，通过这样的压缩解压可能会造成在服务器中文件权限变更，解压之后切记将所有单个档案文件权限设置为644，文件夹权限设定为755。

### 第二步，备份数据库

MYSQL数据库备份大家都知道使用phpMyadmin导入导出功能，在使用phpMyadmin过程中大家总会因为编码的问题费经脑筋，所以我们推荐使用一款叫Navicat的客户端软件来操作备份转移，可以像在Windows中一样使用鼠标操作，详情请参阅：『[MYSQL数据库迁移利器Navicat使用教程](mysql-navicat-info.md)。』下面以本地服务器为示例打开Navicat，具体备份[Joomla!](http://www.Joomla178.com/) 的数据库如下：

1、新建连接，本地MYSQL通常没有设置密码，点击确定即可（如果是远程服务器，需要服务器支持远程数据库连接，有的VPS比如kloxo、cpanel面板，需要设定本机IP为白名单才能连接

![276d8391f626cb90cbcd8730986c0a83.png](../assets/9431d3b9cde50a2a1329.png)

![39ad2f0dfefe645458b668198fe44383.png](../assets/8f3f568d0cbc287dc4ff.png)

2、连接成功随便点击其中一个数据库即可看到下图数据库对应的右侧数据表！

![0dcd10fe0052b802f55b33cef13b8b2f.png](../assets/085f3d7bbde6c205cc3d.png)

3、全选右侧的数据表，右击弹出菜单中选择“转储 SQL 文件”。

![52d8384c325dacd889749dcece268d7c.png](../assets/6ea054a9e9e1b2aede47.png)

4、保证文件格式为.sql格式，弹出转储进度

![c848518e5c82d440a1351fd5637c5ef8.png](../assets/b43d04c74b226a6a9397.png)

5、最后进度框中会显示[Msg] [Dtf] Finished - Successfully 即表示转存完成！然后通过服务器/虚拟主机中的phpMyadmin功能就可以导入这个back.sql文件。

### 第三步，迁移数据库

1、在上面第三步第1点中，再建立一个远程数据库的连接，请保证在服务器/虚拟主机控制面板中预先建立好一个数据库，这样再用Navicat连接远程数据库才能看到。

2、在上面第三步第3点中，全选本地数据库中的表，然后右击复制（注意不是复制表），或者ctrl+C复制所有表

![98bcebd557a4b16ebd39237a3303c4cf.png](../assets/7d6891f3588a5127d4bf.png)

3、在第1步中建立的远程数据库中打开建立好的空数据库，在右侧空白处，右击粘贴表，或者ctrl+V复制刚才在剪贴板中的表

![joomla-backup-mysql-step7.png](../assets/a36f5a2b6a9db6e1211a.png)

4、如果需要确认，就一路默认下来就可以了！

5、非常重要的一点补充，所有的数据库操作后，请仔细检查数据库的编码、校对，右击数据库查看数据库属性，确认是utf8 -- UTF-8 Unicode编码，校对是utf8\_general\_ci

![joomla-backup-mysql-step8](../assets/a67a90d4e9ab377a0148.png)

### 第四步，修改配置文件configraution.php

6个重要的数据库配置参数。

**[Joomla!](http://www.Joomla178.com/) 1.5.x版本如下：**

```
var $host = 'localhost'; //通常是locahostvar $user = 'user'; //数据库的用户名var $password = '12345678'; //数据库的密码var $db = 'dataname'; //数据库名称var $dbprefix = 'joc_'; //数据库表前缀var $log_path = '/home/www/joomla/logs'; //根据服务器实际路径为准var $tmp_path = '/home/www/joomla/tmp'; //根据服务器实际路径为准
```

**[Joomla!](http://www.Joomla178.com/) 2.5.x之后的版本如下：**

```
public $host = 'localhost'; //通常是locahostpublic $user = 'user'; //数据库的用户名public $password = '12345678'; //数据库的密码public $db = 'dataname'; //数据库名称public $dbprefix = 'p3axh_';//数据库表前缀public $log_path = '/home/www/joomla/logs'; //根据服务器实际路径为准public $tmp_path = '/home/www/joomla/tmp'; //根据服务器实际路径为准
```

配置完成后保存configraution.php。

这样就完成了整个网站的数据备份、迁移。

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla!网站迁移备份全过程](http://www.joomla178.com/joomla-share/research-and-development/joomla-backup-all-step.html)
