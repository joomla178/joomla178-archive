---
title: "Ubuntu安装Mongodb时公钥问题错误"
source: "http://www.joomla178.com/joomla-share/front-end/ubuntu-mongodb-ipc-connect-call-failed.html"
category: "前端开发"
author: "Jiang"
date: "2019-02-18"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Ubuntu安装Mongodb时公钥问题错误

因Mongo的不同版本存在不同的公钥，笔者使用Windows 10子系统Ubuntu安装Mongo添加源时抛出错误代码：`gpg: connecting dirmngr at '/tmp/apt-key-gpghome.tspkKKl2KO/S.dirmngr' failed: IPC connect call failed`，这里问题本质并不是Dirmngr问题，而是Mongodb公钥问题。

根据 [WSL Ubuntu 安装MongoDb 4.0导入公钥时遇到一个坑](https://www.7xcode.com/archives/129.html) 文中解决方案，该文作者所提为mongo4.0，本文涉及到mongo3.6，因此使用其提供#查找公钥方法：

### 第一步：搜索对应版本公钥

浏览器中打开网址：`http://keyserver.ubuntu.com/pks/lookup?search=mongodb`，找到mongo3.6（浏览器CTRL+F查看3.6），点击`91FA4AD5`

点击打开后即是公钥内容`Public Key Server -- Get "0x58712a2291fa4ad5"` ，复制其中的`0x58712a2291fa4ad5`

### 第二步：导入公钥

根据上述字符串，组成下述代码，并执行

`` curl -sL "http://keyserver.ubuntu.com/pks/lookup?op=get&search=0x58712a2291fa4ad5"| `sudo apt-key add ``

导入成功后返回`OK`字样，接着执行

```shell
sudo apt-get install
sudo apt-get instll -y mongodb-org
```

完结

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Ubuntu安装Mongodb时公钥问题错误](http://www.joomla178.com/joomla-share/front-end/ubuntu-mongodb-ipc-connect-call-failed.html)
