---
title: "ZOO实用手册 - 升级ZOO程序"
source: "http://www.joomla178.com/joomla-share/zoo-handbook/zoo-handbook-update-zoo.html"
category: "ZOO实用手册"
author: ""
date: "2013-08-29"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# ZOO实用手册 - 升级ZOO程序

![zoo_apps.jpg](../assets/eff724f1ead4960ec1b5.jpg)

本系列教学转自[OKJoomla](http://www.okjoomla.com/companies/)，该系列教程由OKJoomla站长编写

### 一.升级ZOO组件

ZOO两个版本的升级方法完全相同。ZOO有两个版本，一个是免费版本，包含APP：Blog与Pages。一个是付费版本，除Blog与Pages外，还包含其他App组合。

下面我们来分享如何升级ZOO组件：

- 备份旧网站（文件与数据库文件）
- 下载最新版本的ZOO
- 进入页面： Joomla后台 》Extensions》Install/Uninstall，选择上传安装即可。

就这么简单，安装后，ZOO组件，以及所有语言文件，模块以及插件都已经更新到了最新版本。

注：ZOO升级的过程中，ZOO所附带的APP也将同步升级，所以如果您之前自定义过APP的话，那么您所修改的文件(PHP, CSS, Images, 等等)可能会在升级的过程中丢失。因此，我们建议，将您修改过的APP进行复制并重命名，这样升级的过程中，您的自定义文件就不会丢失了。

结束升级后，我们需要清空浏览缓存，以及Joomla缓存。如何清空Joomla缓存：Joomla administration » Tools » Clean Cache.

如果升级安装的过程中，遇到了这样的错误代码：“Fatal error: Maximum execution time of 30 seconds exceeded in ..... on line .....”，我们需要进行“文件夹安装”ZOO。

- 下载最新版本的ZOO到您的电脑，并将其解压
- 使用FTP软件，上传解压后的ZOO左右文件到 您的Joomla网站目录中/tmp 文件夹中
- 进入页面：Joomla后台 » Extensions » Install/Uninstall，选择 “从文件夹安装”，之后选择您上传到 /tmp 中的ZOO文件夹
- 点击 安装按钮 ，系统将会进行安装ZOO软件

### 二. 升级ZOO的APP

当升级ZOO组件的同时，APP也会自动进行更新。

APP存放在安装文件夹 /applications中。

我们建议您通过ZOO组件升级顺带升级APP，当然如果您只想单独升级某一个APP的话，那么可以按照下面的步骤进行操作：

- 备份App
- 进入 Components » ZOO » App manager (选择Tab表单，进入App manager)
- 选择App文件，并点击安装（Install）

注：升级过程将替换掉您对原APP进行的所有更改，但您的设置将会被保留。（Types与Element的设置文件）。

要想手动更新新版的Types设置，需要进入该APP的Types文件夹（applications/APPNAME/types/），复制其中的文件。

要想手动更新新版的Element设置，需要进入该APP的Element文件夹（applications/APPNAME/templates/TEMPLATENAME/renderer/item），复制其中的文件。

### 三.升级ZOO的插件与模块

当升级ZOO组件的同时，插件与模块也会自动进行更新

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [ZOO实用手册 - 升级ZOO程序](http://www.joomla178.com/joomla-share/zoo-handbook/zoo-handbook-update-zoo.html)
