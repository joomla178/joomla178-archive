---
title: "Joomla! 3 十步建站第二步：下载和安装Joomla!"
source: "http://www.joomla178.com/joomla-share/joomla3-in-10-easy-steps/joomla3-in-10-easy-steps-down-install-joomla.html"
category: "Joomla! 3 十步建站"
author: ""
date: "2013-04-26"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla! 3 十步建站第二步：下载和安装Joomla!

Multithumb found errors on this page:  
  
There was a problem loading image http://farm9.staticflickr.com/8177/7996865501\_996aa63766.jpg  
There was a problem loading image http://farm9.staticflickr.com/8456/7996826195\_31164a4be7.jpg  
There was a problem loading image http://farm9.staticflickr.com/8450/7996833126\_5c7a738e45.jpg  
There was a problem loading image http://farm9.staticflickr.com/8455/7996825871\_ec8680aa7d.jpg  
There was a problem loading image http://farm9.staticflickr.com/8033/7996832754\_552655a249.jpg  
There was a problem loading image http://farm9.staticflickr.com/8454/7996825443\_abc38802a9.jpg  
There was a problem loading image http://farm9.staticflickr.com/8454/8026109221\_73ba8d2a6e.jpg  
There was a problem loading image http://farm9.staticflickr.com/8042/7996832242\_e8998d51c5.jpg  
There was a problem loading image http://farm9.staticflickr.com/8034/7996832360\_54231a552a.jpg  
There was a problem loading image http://farm9.staticflickr.com/8444/7996832604\_1fdc15d6c8.jpg  
There was a problem loading image http://farm9.staticflickr.com/8179/8008659808\_50f80e0edf.jpg  
There was a problem loading image http://farm9.staticflickr.com/8447/7996881068\_4477800a64.jpg  
There was a problem loading image http://farm9.staticflickr.com/8171/7996880924\_7b126d244d.jpg

### 2. 下载和安装Joomla

本系列教学转自 [Cocoate免费书库](http://cocoate.com/j3/what-is-joomla) ，英文原著由[Hagen Graf](http://cocoate.com/user/hagen-graf)编写，中文翻译由[Derek Joe](http://cocoate.com/zh-hans/derek-joe)完成

迷茫……下载什么？到哪下载？上哪去安装？为什么要安装？安装什么？  
 要把Joomla安装到您的电脑上（我们常称呼你的电脑为“本地”（local）），您就必须安装您自己的网络，也就是您必须要有一个浏览器、一个web服务器、一个PHP环境以及一个Joomla支持的数据系统。我们称之为一个解决方案栈和一个客户机/服务器系统。  
 解决方案栈是指为了实现Joomla网站的完整功能所需的一套软件系统或组件：

- 服务器的操作系统（Linux、Windows、OSX）
- web服务器（Apache、IIS）
- 数据库（MySQL、PostgreSQL）
- 脚本语言（PHP）

您可以在家自己搭建一个解决方案栈，您也可以购买或从主机商提供的规格繁多的虚拟主机里租用一个。Joomla 3.x所需的解决方案栈（我们也常称之为“环境要求”）请见*图1*。

| **软件** | **最低要求** |
| --- | --- |
| PHP | 5.3.1 + |
| MySQL （InnoDB support required） | 5.1 + |
| Apache  （需要有mod\_mysql、mod\_xml、and mod\_zlib） | 2.x + |
| Microsoft IIS | 7 |

*图 1：Joomla 3.x*的环境要求  
   
 所有的PHP环境都需要考虑类似的因素，因此我推荐你阅读这一章的内容：[PHP环境的安装变量](http://cocoate.com/node/6540)。  
 如果解决方案栈已搭建完毕并可以正常运行，我们就得到了一台服务器。这台服务器可以是您的电脑，也可以说远程的某台电脑。网站的所有访客和注册用户都是使用他们电脑中的浏览器访问您的Joomla网站。我们称他们为客户端。  
   
 “经典” LAMP解决方案栈看起来如*图1*。

![LAMPP Architecture](http://farm9.staticflickr.com/8177/7996865501_996aa63766.jpg "LAMPP Architecture")

*图1： LAMP解决方案栈*

## Joomla Web安装器

有了web安装器，我们可以在几分钟内完成Joomla的安装：  
 把Joomla!文件从压缩包解压到网站的根目录，并使用Joomla! web安装器做好配置，一切就这么简单！  
 从[joomla.org](http://www.joomla.org/download.html)下载Joomla! 3，并把文件解包到web服务器的根目录（例如：/htdocs）。  
 从现在开始，在Joomla! web安装器就绪的情况下，您很快就能完成安装：使用浏览器访问<http://localhost/>。

### 绊脚石

*这个话题很复杂，因为实在有太多的主机商和更多的主机类型，再加上PHP、MySQL版本和主机管理工具，等等。安装中的要点是：*

- *一个激活的PHP安全模式（Safe Mode），防止非法写入文件。*
- *“禁用了”Apache web服务器的重写路径 因为所谓的Apache Rewrite Engine （mod\_rewrite）未激活。*
- *Linux和OSX的目录权限设置，和Windows不一样。*

*基本上，几乎总能让您完成安装的最简单的方式如下：*

- *从[Joomla.org](http://www.joomla.org/download.html)下载安装包到你的电脑，并解压所有文件到一个临时目录。*
- *通过FTP将以上所有文件上传到你租用的主机或者移动到你本地的安装目录里。这些文件必须处于公共目录，这些目录的名称通常为htdocs、public\_html或html。如果这些目录已经安装了其它东西，您可以指定一个子目录来放置Joomla文件。许多主机允许您将网站域名解析到一个指定的目录。*
- *您必须要知道您的数据库的名称。多数情况下，在您租用的主机里已经包含了一个或多个数据库。有时候主机商会直接告诉您数据库的用户名、数据库的名称以及密码；有时候您要先自己设置这些。通常您通过浏览器能够访问的一个界面即可完成相关设置。而这些是Joomla web安装器必需的信息。*

## 安装前检查

安装前检查用于帮助您确定您的服务器环境是否符合Joomla安装的要求。注意页面上方有安装过程的语言的选择。如果在这个页面您发现有红色标记，那么很不幸您的解决方案栈的配置不恰当并且安装器会拒绝安装Joomla。实际情况依据您的环境配置，会有不同的要求。Joomla考察的是web服务器（我们的示例中使用的是Apache）、PHP和操作系统的配置。当使用Unix类的操作系统（如Linux、Mac OS X）时，您要特别注意[文件权限](http://cocoate.com/node/3232)。该设置决定着在Joomla安装中，能否根据您的设置而生成文件configuration.php。如果安装器无法在文件夹中执行写入操作，Joomla的安装就无法完成。如果碰到这种情况，应该马上修改配置后，通过刷新页面来重新检查。

![Pre Installation](http://farm9.staticflickr.com/8456/7996826195_31164a4be7.jpg "Pre Installation")

*图2: 安装前检查*

## 第一步：配置

在这个配置页面，您必须命名您的网站并填写网站的描述，以及超级管理员的相关资料。最下方还有个按钮决定网站安装完成后，是马上开放，还是先关闭而只让网站管理员访问。这一设置在您将网站直接安装到您的实际主机里的时候，是非常实用的（*图3*）。

![Main Configuration](http://farm9.staticflickr.com/8450/7996833126_5c7a738e45.jpg "Main Configuration")

*图3: 安装器 - 配置页面*

## 第二步：数据库

Joomla可以让您选用多种数据库。反言之，您要能确定到底使用哪种数据库服务器，然后您必须填写数据库的相关参数（*图4*）。在您本地的环境里，您创建多少个数据库都行。  
 在Ubuntu Linux里使用MAMP软件包时，您的MySQL用户名为root。用户root是MySQL的管理员，在MySQL系统里无所不能。该用户的密码则与您的服务器环境相关（[XAMPP](http://www.apachefriends.org/)勿需密码，[MAMP](http://www.mamp.info/)的密码也是“root”）。  
 当您在使用实际的主机时，您的主机商通常会为您提供相对应的信息。

![Database](http://farm9.staticflickr.com/8455/7996825871_ec8680aa7d.jpg "Database")

*图4: 安装器 – 数据库设置*

在你电脑（本地）进行安装时，请按下面的信息填写：

- 主机名：localhost
- 用户名：root
- 密码：[亲，这只有您自己知道]

现在请填写数据库名称。当您在使用实际的主机时，您的主机商通常会为您提供相对应的信息，并且您只能严格使用这些信息。如果您有数据库服务器的根权限（root permission），您可以任意填写一个数据库名称（当然最好不要和您已经在使用的其它数据库重名），Joomla随后会创建这个数据库。  
 您可以选择决定当该数据库里存在数据表时，是被清理掉，还是在以前的数据表前面加“*bak\_*”后备份在原处。  
 数据表的前缀是很实用的。web安装器能在每个表前面添加你给定的前缀，但默认情况下，它会建议性地使用一个随机生成的前缀，如“*w02rh\_*”。采用前缀的原因很简单，有时候您只能从主机商那里获得一个MySQL数据库。没有前缀你就没法运行两个或更多的Joomla网站。有了前缀就能够区分出多组数据表（如*w01client\_*、*w02client\_*）。因此你最好采用随机生成的前缀。 前缀"bak\_" 常用于表明这是数据表备份。

## 第三步 – 最终确定

第三步Joomla会告诉您您的网站配置的概况，并询问您是否要安装示范数据（*图4*）。

![Finalisation](http://farm9.staticflickr.com/8033/7996832754_552655a249.jpg "Finalisation")

*图4: 最终确定*

Joomla 2.5只有一组示范数据供您安装，Joomla 3则提供了多种选择。“示范数据”不但能为您安装博客风格的示范内容（*图5*）、手册风格的示范内容（*图6*）、学习型示范数据（*图7*）、默认示范数据（*图8*），而且从名称就知道实际上这些内容相对应的页面风格也是不同的。

![Blog Example Data](http://farm9.staticflickr.com/8454/7996825443_abc38802a9.jpg "Blog Example Data")

*图5: 博客风格的示范内容*

![Brochure Website](http://farm9.staticflickr.com/8454/8026109221_73ba8d2a6e.jpg "Brochure Website")

*图6: 手册风格的示范内容*

![Learn Joomla Example Data](http://farm9.staticflickr.com/8042/7996832242_e8998d51c5.jpg "Learn Joomla Example Data")

图7: 学习型示范数据

![Default Example Data](http://farm9.staticflickr.com/8034/7996832360_54231a552a.jpg "Default Example Data")

*图8: 默认示范数据*

您可以按照您的需要和基础，安装适当的示范数据。  
 不过安装完成后，您是无法在不同种类的示范数据中切换到。也就是说，你只能选择一种类型。  
 当然您也可选择不安装任何示范数据。如果您知道如何使用Joomla，“不安装示范数据”其实是个很好的选择。  
 我也将选择一个“裸奔”的Joomla（即不安装示范数据）作为接下来几章的基础。  
 没有示范数据，您将更容易理解接下来的内容。  
 选择您需要的示范内容，然后点击“安装”，Joomla就会安装好数据库并为您配置好整个网站（*图9*）。

![Congratulations](http://farm9.staticflickr.com/8444/7996832604_1fdc15d6c8.jpg "Congratulations")

*图9: Joomla完成安装*

为安全起见，安装完成后，必须删除安装目录：请点击“删除安装目录”。安装目录删除后，您就可以直接访问网站前台或者后台管理（地址为：域名*/administrator*）。我安装后的网站如*图10*。

!['Naked Joomla'](http://farm9.staticflickr.com/8179/8008659808_50f80e0edf.jpg "'Naked Joomla'")

*图10: 没有安装示范数据的Joomla网站*

输入如下地址即可访问Joomla的控制面板：

```
http://your_domain.tld/administrator
```

马上会给你显示一个登录界面，并且您可以选择自己想要的后台管理的语言（*图11*）。成功登录后它就会以该语言为您开启后台管理。（*图12*）。

![Administrator Login](http://farm9.staticflickr.com/8447/7996881068_4477800a64.jpg "Administrator Login")

*图11: 登录界面*

![Control Panel](http://farm9.staticflickr.com/8171/7996880924_7b126d244d.jpg "Control Panel")

*图12: 控制面板*

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla! 3 十步建站第二步：下载和安装Joomla!](http://www.joomla178.com/joomla-share/joomla3-in-10-easy-steps/joomla3-in-10-easy-steps-down-install-joomla.html)
