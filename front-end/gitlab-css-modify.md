---
title: "GitLab平台自身字体样式修改"
source: "http://www.joomla178.com/joomla-share/front-end/gitlab-css-modify.html"
category: "前端开发"
author: "Jiang"
date: "2015-11-18"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# GitLab平台自身字体样式修改

GitHub无疑是开发者最受欢迎的平台，最近公司有项目需要寻求一个综合解决方案，于是寻得GitLab这个开源平台，几经周折在CentOS7下按照Gitlab的一键安装包成功地安装在内网服务器下，使用过程中因为其字体样式均为默认，对中文显示外观不太友好，下决定找到它并改掉它。

由于Gitlab采用的是Sass预编译处理工具来处理样式，运行大概原理是生成了一些css缓存数据，开发者开具并未找到其路径，但是有个目标是找到其sass文件必然能改掉它的css字体。

说了这么多，其实重点是把路径说出来：/opt/gitlab/embedded/service/gitlab-rails/app/assets/stylesheets/framework/variables.scss，原来是一个bootstrap的变量库，拉到最底部，尽情地修改样式了。

修改完要重新sudo gitlab-ctl reconfigure一次

2016年1月19日补充

之前记在笔记上了，上次并未提到UI缓存重建，现在补充一下。

完成上述工作并没有编译最新的样式缓存，在ssh中继续执行命令：

进入目录：/opt/gitlab/embedded/service/gitlab-rails，输入以下命令进行UI缓存重建

```
bundle exec rake assets:precompile RAILS_ENV=production
```

生成后的UI缓存位于：/opt/gitlab/embedded/service/gitlab-rails/public/

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [GitLab平台自身字体样式修改](http://www.joomla178.com/joomla-share/front-end/gitlab-css-modify.html)
