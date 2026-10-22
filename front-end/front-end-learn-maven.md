---
title: "前端需要知道的maven常用命令"
source: "http://www.joomla178.com/joomla-share/front-end/front-end-learn-maven.html"
category: "前端开发"
author: "Jiang"
date: "2016-07-06"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 前端需要知道的maven常用命令

最近新东家的前端开发模式主要基于JAVA + Eclipse + Maven + jetty方式调试，而且作为前端人员，需要在本机配置这样的调试环境，笔者只因Mac下的Eclipse太过丑陋，改用IDEA来配置调试环境、Sublime Text编辑代码，由于项目成员大多不用IDEA，所以在每次更新项目后，我总能遇到一大堆错误，纠其根本主要是因为Maven原因。

通过IDEA的功能菜单并未解决问题，无奈想到Maven类似SVN，可通过命令行工具来下载、编译等，前端用到的也就是清理、下载、编译等指令即可！

当SVN更新过项目之后，需要清理之前编译的文件，执行指令：

```
mvn clean
```

然后再把Maven仓库的代码拉取到本机，执行命令：

```
mvn dependency:sources -DdownloadSources=true -DdownloadJavadocs=true
```

拉取完代码之后再执行编译命令：

```
mvn compile
```

编译好之后再执行打包命令：

```
## 普通打包
mvn package
## 跳过测试打包
mvn package -Dmaven.test.skip=ture
```

抽时间再做一下IDEA+Maven配置教程

前端开发人员用到的命令也就这么多了，其它的命令可参考：

<http://www.cnblogs.com/adolfmc/archive/2012/07/31/2616908.html>

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [前端需要知道的maven常用命令](http://www.joomla178.com/joomla-share/front-end/front-end-learn-maven.html)
