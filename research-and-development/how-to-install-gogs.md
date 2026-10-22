---
title: "安装Gogs源码版遇到的麻烦"
source: "http://www.joomla178.com/joomla-share/research-and-development/how-to-install-gogs.html"
category: "研究开发"
author: "Jiang"
date: "2016-03-03"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 安装Gogs源码版遇到的麻烦

GitLab太吃内存，只适合内网服务器跑起来，在阿里云的1G内存版服务器跑，总是内存不够！后发现中文化的Git WEB服务器程序Gogs，二话不说，看官网安装教程，但是由于该开源采用的是Go语言，所以安装过程掉坑了。

前往官方文档：<https://gogs.io/docs/installation/install_from_source>，装Git就不多赘述，安装Go语言倒也还好，至少wget <https://storage.googleapis.com/golang/go$VERSION.$OS-$ARCH.tar.gz> 还是很顺利，没有受到影响，往下就开始坑了。

### 安装Gogs

第一条指令

```
# 下载并安装依赖 $ go get -u github.com/gogits/gogs
```

开始下载还是蛮正常的，查看服务器目录 /home/git/go/src，能看到github.com和gopkg.in，但是golang.org还是没有，命令出现报错：

```
package golang.org/x/net/html: unrecognized import path "golang.org/x/net/html"
# cd .; git clone https://github.com/nfnt/resize /home/git/go/src/github.com/nfnt/resize
Cloning into '/home/git/go/src/github.com/nfnt/resize'...
fatal: unable to access 'https://github.com/nfnt/resize/': Could not resolve host: github.com
package github.com/nfnt/resize: exit status 128
# cd .; git clone https://github.com/sergi/go-diff /home/git/go/src/github.com/sergi/go-diff
Cloning into '/home/git/go/src/github.com/sergi/go-diff'...
fatal: unable to access 'https://github.com/sergi/go-diff/': Could not resolve host: github.com
package github.com/sergi/go-diff/diffmatchpatch: exit status 128
package golang.org/x/crypto/ssh: unrecognized import path "golang.org/x/crypto/ssh"
package golang.org/x/net/html/charset: unrecognized import path "golang.org/x/net/html/charset"
package golang.org/x/text/transform: unrecognized import path "golang.org/x/text/transform"
```

大概意思是 golang.org 的三个源码crypto,net,text没有下载成功，另外github上的resize和go-diff也没有下载成功，这样就好对症下药了

不要切换账户，仍然在git下使用下述命令

前往<https://github.com/nfnt/resize> 下载resize，按文档下载：

```
go get github.com/nfnt/resize
```

前往<https://github.com/sergi/go-diff> 下载go-diff，按文档下载：

```
go get github.com/sergi/go-diff/diffmatchpatch
```

不一会两个依赖都会安装成功

### 最难的是golang的几个依赖

在这里还是要很遗憾的说明，crypto,net,text 必然要使用代理才能下载到

笔者用的是本机电脑下载的资源，然后再上传到服务器上

```
git clone https://go.googlesource.com/crypto
git clone https://go.googlesource.com/net
git clone https://go.googlesource.com/text
```

下载成功之后都上传至服务器/home/git/go/src/golang.org/x/目录下，修改用户组

```
chown -R git:git /home/git/go/src/golang.org/x
```

再回到官方安装教学

```
# 构建主程序
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build
```

执行完这条命令最郁闷的是啥提示也没有，因为下一步还要往下看

```
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

再输入IP或域名:3000 可以看到进入安装界面了，这也是以后启用这个服务的指令

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [安装Gogs源码版遇到的麻烦](http://www.joomla178.com/joomla-share/research-and-development/how-to-install-gogs.html)
