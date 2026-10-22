---
title: "同一台电脑关于多个SSH KEY管理"
source: "http://www.joomla178.com/joomla-share/research-and-development/one-pc-multi-ssh-key.html"
category: "研究开发"
author: "Jiang"
date: "2016-03-03"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 同一台电脑关于多个SSH KEY管理

使用环境:关于同一台电脑LInux系统下使用多个SSH key 切换使用(或者多用户使用ssh提交代码)

要求,可以创建不同的 PUBLIC KEY ,根据下面步骤设置.

(1)比如有aaa,bbb,ccc 三个帐号需要生成不同的 PUBLIC KEY

```
$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa):/root/.ssh/id_rsa_aaa
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /root/.ssh/id_rsa_aaa.
Your public key has been saved in /root/.ssh/id_rsa_aaa.pub.
The key fingerprint is:
9b:92:f6:1f:d2:72:bd:72:19:45:42:5f:e4:65:33:64 root@AY140122145815620396Z
The key's randomart image is:
+--[ RSA 2048]----+
|           .. .E=|
|            ..o++|
|             o. .|
|              .  |
|        S    .   |
|       . + ..    |
|      + = + .o   |
|     . o +..o.   |
|        ...o.    |
+-----------------+
```

进过上面的shell 我们在 /root/.ssh/ 目录下创建 id\_rsa\_aaa  私钥 和 id\_rsa\_aaa.pub 公钥

注意这里

```
Enter file in which to save the key (/root/.ssh/id_rsa):/root/.ssh/id_rsa_aaa  #设置路径,如果
```

(2)按照上面的步骤逐个生成 bbb 和 ccc 对应的公钥和私钥 ........

(3)查看系统ssh-key代理,执行如下命令

```
$ ssh-add -l
Could not open a connection to your authentication agent.
如果发现上面的提示,说明系统代理里没有任何key,执行如下操作
exec ssh-agent bash
```

如果系统已经有ssh-key 代理 ,执行下面的命令可以删除

```
$ ssh-add -D
```

(4)把 .ssh 目录下的3个私钥添加的 ssh-agent

```
$ ssh-add ~/.ssh/id_rsa_aaa
$ ssh-add ~/.ssh/id_rsa_bbb
$ ssh-add ~/.ssh/id_rsa_ccc
```

依次执行上面三条shell 把三个私钥添加到 ssh-key 代理里面

(5)打开github 或者 开源中国 ssh 管理页面把 对应的公钥提交保存到代码管理服务器 (.pub 结尾)

(6)在 .ssh 目录创建 config 配置文件

```
nano ~/.ssh/config
```

输入如下配置信息

```
#aaa  (github 配置)
Host aaa
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_aaa

#bbb  (开源中国 配置)
Host bbb
    HostName git.oschina.net
    User git
    IdentityFile ~/.ssh/id_rsa_bbb

#ccc
........
```

(6)记住上面一步 Host 里设置的别名,开始克隆项目,以开源中国为例

```
git clone 该 Email 地址已受到反垃圾邮件插件保护。要显示它需要在浏览器中启用 JavaScript。:userName/projectName.git
```

到此为止多个ssh-key 已经可以同时使用.

文章来自：[一介布衣](http://yijiebuyi.com/blog/f18d38eb7cfee860c117d629fdb16faf.html)

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [同一台电脑关于多个SSH KEY管理](http://www.joomla178.com/joomla-share/research-and-development/one-pc-multi-ssh-key.html)
