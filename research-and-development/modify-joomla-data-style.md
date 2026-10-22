---
title: "更改Joomla的日期、时间格式"
source: "http://www.joomla178.com/joomla-share/research-and-development/modify-joomla-data-style.html"
category: "研究开发"
author: "Jiang"
date: "2013-07-26"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 更改Joomla的日期、时间格式

Multithumb found errors on this page:  
  
There was a problem loading image http://www.cn4jd.com/sites/default/files/get\_image/dateformat\_search.png  
There was a problem loading image http://www.cn4jd.com/sites/default/files/get\_image/dateformat\_text.png  
There was a problem loading image http://www.cn4jd.com/sites/default/files/get\_image/dateformat\_newdate.png  
There was a problem loading image http://www.cn4jd.com/sites/default/files/get\_image/dateformat\_formatguide.png

文章来自：<http://www.cn4jd.com/change-joomla-s-date-format>

Joomla! 本身是用的标准的国际日期格式，然而，有许多网站需要你创建一个特定的日期格式

此教程中，我将一步一步展示给你如果变更你的文章日期格式

### 1. 创建语言覆盖

![dateformat_search.png](http://www.cn4jd.com/sites/default/files/get_image/dateformat_search.png)

首先你需要创建一个语言覆盖. [You你在这里可以找到如果创建语言覆盖的教程（英文版）](http://www.ostraining.com/blog/joomla/languge-manager/)

1. 前往 Extensions（扩展） -> Language Manager（语言管理）.
2. 点击 Overrides（语言覆盖）选项
3. 点击New（新建）.
4. 选中 "Constant（常数）"选项.
5. 搜索"DATE\_FORMAT\_LC2".
6. 点击常数加载到的搜索结果

### 2. 更改日期格式

![dateformat_text.png](http://www.cn4jd.com/sites/default/files/get_image/dateformat_text.png)

更改这里的文本为你喜欢的日期格式

只需在你喜欢的格式中移除文本和类型

例如, 如果你想日期显示为January 01, 2013, 你需要使用 : F j, Y

### 3. 刷新你的页面

![dateformat_newdate.png](http://www.cn4jd.com/sites/default/files/get_image/dateformat_newdate.png)

祝贺你！现在你的网站有个新的日期格式啦

### 小提示: 日期格式定义

![dateformat_formatguide.png](http://www.cn4jd.com/sites/default/files/get_image/dateformat_formatguide.png)

在上图中展示了显示日期格式的不同的方法

这里有个列表罗列了在Joomla中常用的日期格式字符

- l (小写字母 'L')    星期几，完整的文本格式  （*Sunday* 到 *Saturday）*
- d     月份中的第几天，有前导零的 2 位数字 （ *01* 到 *31）*
- M     三个字母缩写表示的月份  （ *Jan* 到 *Dec）*
- m     数字表示的月份，有前导零 （  *01* 到 *12）*
- F     月份，完整的文本格式，例如 January 或者 March  （ *January* 到 *December)*
- Y     4 位数字完整表示的年份 例如：(*1999* 或 *2003)*
- H     小时，24 小时格式，有前导零 ( *00* 到 *23)*
- i     有前导零的分钟数 ( *00* 到 *59*>)

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [更改Joomla的日期、时间格式](http://www.joomla178.com/joomla-share/research-and-development/modify-joomla-data-style.html)
