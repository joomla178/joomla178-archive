---
title: "GitLab升级维护及升级后报500错误"
source: "http://www.joomla178.com/joomla-share/research-and-development/gitlab-upgrade-problem.html"
category: "研究开发"
author: "Jiang"
date: "2016-01-19"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# GitLab升级维护及升级后报500错误

早先给公司内网搭建了一套基于Git的服务器GitLab，GitLab升级包更新较快，笔者在升级过程中记录下爬的教程以及遇到了不少的问题，现在分享给出来以供需要时参考。

积攒多年的血泪教训，升级之前做备份，另外笔者安装的是一键安装包，所以按照一键安装包的升级方式来操作，参考GitLab官方升级教程：<https://about.gitlab.com/upgrade-to-package-repository/> 但原文过于简单，不太放心，另外参考了英文帮助：<https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/doc/update/README.md#updating-from-gitlab-66-and-higher-to-the-latest-version>

### 备份GitLab

#### 修改默认备份目录：

默认备份目录是/var/opt/gitlab/backups，如果不想修改可以略过此步，编辑文件/etc/gitlab/gitlab.rb，找到代码

```
# gitlab_rails['backup_path'] = "/var/opt/gitlab/backups"
```

移除该行代码前的注释并修改目录：

```
# gitlab_rails['backup_path'] = "/home/backups"
```

在修改完后需要键入gitlab-ctl reconfigure命令重载配置文件即可。

#### 执行备份：

直接执行下述代码：

```
gitlab-rake gitlab:backup:create
```

显示执行成功：

```
Dumping database ...
Dumping PostgreSQL database gitlabhq_production ... [DONE]
done
Dumping repositories ...
 * group/project ... [DONE]
done
Dumping uploads ...
done
Dumping builds ...
done
Dumping artifacts ...
done
Dumping lfs objects ...
done
Creating backup archive: 1453173545_gitlab_backup.tar ... done
Uploading backup archive to remote storage  ... skipped
Deleting tmp directories ... done
done
done
done
done
done
done
Deleting old backups ... skipping
```

### 升级GitLab

#### 下载完整包

笔者想过下载个很小的升级包是不是就可以了，答案是否定的，而且由于一些原因，下载比较费力，老老实实用迅雷去下载吧。

先前往packages页面：<https://packages.gitlab.com/gitlab/gitlab-ce>，找到自己对应系统，笔者是CentOS7，下载rpm包

点击gitlab-ce-8.3.4-ce.0.el7.x86\_64.rpm进入下载页，点右上角Download，生成下载链接后用迅雷下载，否则龟速

上传gitlab-ce-8.3.4-ce.0.el7.x86\_64.rpm到服务器/root目录下

#### 开始升级

回到linux命令行，依次键入命令（最后一步是备份意思，可以活力）

```
sudo gitlab-ctl stop unicorn
sudo gitlab-ctl stop sidekiq
sudo gitlab-ctl stop nginx
sudo gitlab-rake gitlab:backup:create
```

然后键入安装命令

```
# Ubuntu/Debian系统:
sudo dpkg -i gitlab_x.x.x-omnibus.xxx.deb

# CentOS系统:
sudo rpm -Uvh gitlab-x.x.x_xxx.rpm
```

耐心等待100%完成后，键入重建和重启命令：

```
sudo gitlab-ctl reconfigure
sudo gitlab-ctl restart
```

### 遇到的问题

#### 进程占用

在reconfigure时遇到错误： Chef client 11936 is running，查得Chef client进程占用，查进程列表，键入ps命令

```
ps
```

相关gitlab的命令全杀掉，kill -9 11936，-9意思是强制结束进程，11936是进程pid

```
kill -9 11936
```

然后重新重建和重启，完美地完成

#### 500错误

前面高兴的太早，访问GitLab发现报500错误，爬文得知大意为DB数据关系错误，需要升级数据库关系

输入以下指令查看数据升级状态

```
sudo gitlab-rake db:migrate:status
```

果然发现有一些显示为Down，显示为Up即表示正常同，再执行数据库关系升级

```
sudo gitlab-rake db:migrate
```

执行完成再重复重建、重启命令，问题解决

500错误解决参考出处：<https://stackoverflow.com/questions/26224649/gitlab-error-500-after-updating-when-viewing-projects?rq=1>

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [GitLab升级维护及升级后报500错误](http://www.joomla178.com/joomla-share/research-and-development/gitlab-upgrade-problem.html)
