---
title: "链接丢失itemid导致模块无法显示的解决方法"
source: "http://www.joomla178.com/joomla-share/research-and-development/lost-item-id.html"
category: "研究开发"
author: "Jiang"
date: "2011-11-16"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 链接丢失itemid导致模块无法显示的解决方法

最近做网站，发现了一个itemid经常丢失的问题，网上搜资料未果，在别的q群高人指点下终于得到解决。

**joomla版本：**1.5.x中文

**问题描述：**

在已有的分类添加了一个新文章后，在前台列表中打开该文章，文章链接中没有itemid，所以导致必要的菜单选项没有出现。

**解决办法：**

1、后台中打开菜单选项  
2、创建一个新菜单，比如“虚拟菜单”，你也可以选择其他名字，不是为了真正发布，只是一个虚拟菜单项目，为了给文章加itemid。  
3、进入新建的虚拟菜单  
4、点击创建  
5、创建内部链接—文章—单元—单元布局  
6、在右面的第一项选择丢失itemid的那个单元  
7、填好菜单的名称和别名  
8、保存

然后最后一步是将丢失itemid的那个菜单模块指到新建的这个“虚拟菜单”菜单上显示，然后再发篇文章就可以看到菜单出来了~~

E文原文如下：  
Procedure -  
-> Select Menu Manager from Menus link  
-> Create a New Menu Item - E.g. "Dummy Menu" (You can choose any name you want. This is not to publish on any module position. This is just a dummy menu item for the purpose of generating itemid for each article section)  
-> From Menus link select "Dummy Menu"  
-> New  
-> Under Internal Link -> Articles -> Section -> Section Layout  
-> Select first section from right hand side first option  
-> Give a suitable title & alias. I suggest using the title of the section to avoid any confusion.  
-> Save  
-> Repeat this process for each section of articles that you wish to publish on front page.  
-> Problem Solved

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [链接丢失itemid导致模块无法显示的解决方法](http://www.joomla178.com/joomla-share/research-and-development/lost-item-id.html)
