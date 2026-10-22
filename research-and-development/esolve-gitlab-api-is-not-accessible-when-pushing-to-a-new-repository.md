---
title: "解决Gitlab在Git操作中出现 GitLab: API is not accessible 错误"
source: "http://www.joomla178.com/joomla-share/research-and-development/esolve-gitlab-api-is-not-accessible-when-pushing-to-a-new-repository.html"
category: "研究开发"
author: "Jiang"
date: "2016-03-02"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 解决Gitlab在Git操作中出现 GitLab: API is not accessible 错误

在创建源码版的Gitlab服务器时（不是GitLab CE Omnibus版），一切顺利的进行下去，到了开始使用git进行通信时，无论是git clone还是git push都出现了GitLab: API is not accessible 错误提示，查询资料找到了解决办法。

在常规配置文件/home/git/gitlab/config/gitlab.yml中要把host配置正确为主机最终域名（内网配置为IP），这些都是没问题的常规操作

但是笔者忘了配置/home/git/gitlab-shell/config.yml中的 gitlab\_url: <http://localhost/，>此项默认为http://localhost/ 如果不Gitlab服务器配置的是子域名，或者是其它域名，则此项必须修改为最终Gitlab服务器的域名，内网IP如果给Gitlab配置了端口，记住也要将http://localhost改为http://ip:8080这样的带端口形式

最后问题轻松解决

参考资料：<http://stackoverflow.com/questions/31569555/how-to-resolve-gitlab-api-is-not-accessible-when-pushing-to-a-new-repository>

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [解决Gitlab在Git操作中出现 GitLab: API is not accessible 错误](http://www.joomla178.com/joomla-share/research-and-development/esolve-gitlab-api-is-not-accessible-when-pushing-to-a-new-repository.html)
