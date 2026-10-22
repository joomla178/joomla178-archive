---
title: "Joomla的htaccess文件使用范例"
source: "http://www.joomla178.com/joomla-share/research-and-development/how-to-use-joomla-htaccess.html"
category: "研究开发"
author: "lucky"
date: "2012-09-02"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# Joomla的htaccess文件使用范例

英文教程出处：<http://docs.joomla.org/Htaccess_examples_%28security%29>

这是一篇关于joomla的htaccess文件使用的教程文章，教程列举了多个范例供使用者参考。[野草](http://www.ycway.com/)对此教程进行了翻译，但某些地方，可能由于理解不深，翻译得有所偏差，希望大家可以就此指正或交流。

首先，把RewriteEngine设置启用，并设置Options +FollowSymLinks   
在任何情况下，只要您没有指定FollowSymLinks的选项（即Options FollowSymLinks），或者指定了 SymLinksIfOwnerMatch选项，Apache将不得不调用额外的系统函数来检查符号链接。每次针对文件名的请求都将触发一次检查。

如果你没有使用followsymlinks规则而网站访问正常，说明你的服务器配置已经默认调用followsymlinks的重写规则，你无需再为你的htaccess文件定义了。但在有些服务器500 Server Error之后的错误日志中提示需要定义SymLinks使得rewrite重写规则起做用。

# 启用Apache的重写模块

```
RewriteEngine OnOptions +FollowSymLinks
```

用户代理黑名单

#下面列表中的用户代理（浏览器、下载软件、搜索引擎机器人等）可能已经不存在或者不会影响到你的网站。因为互联网日新月异，因此该列表永远不可能是完整的，它只是参照了多个“安全”邮件列表或论坛的讨论，例如  
<http://www.webmasterworld.com/search_engine_spiders/> 。如果你依靠此列表作为你的唯一安全机制是不明智的做法。

```
RewriteCond %{HTTP_USER_AGENT} ^BlackWidow [OR]RewriteCond %{HTTP_USER_AGENT} ^Bot\ mailto: 该 Email 地址已受到反垃圾邮件插件保护。要显示它需要在浏览器中启用 JavaScript。 [OR]RewriteCond %{HTTP_USER_AGENT} ^ChinaClaw [OR]RewriteCond %{HTTP_USER_AGENT} ^Custo [OR]RewriteCond %{HTTP_USER_AGENT} ^DISCo [OR]RewriteCond %{HTTP_USER_AGENT} ^Download\ Demon [OR]RewriteCond %{HTTP_USER_AGENT} ^eCatch [OR]RewriteCond %{HTTP_USER_AGENT} ^EirGrabber [OR]RewriteCond %{HTTP_USER_AGENT} ^EmailSiphon [OR]RewriteCond %{HTTP_USER_AGENT} ^EmailWolf [OR]RewriteCond %{HTTP_USER_AGENT} ^Express\ WebPictures [OR]RewriteCond %{HTTP_USER_AGENT} ^ExtractorPro [OR]RewriteCond %{HTTP_USER_AGENT} ^EyeNetIE [OR]RewriteCond %{HTTP_USER_AGENT} ^FlashGet [OR]RewriteCond %{HTTP_USER_AGENT} ^GetRight [OR]RewriteCond %{HTTP_USER_AGENT} ^GetWeb! [OR]RewriteCond %{HTTP_USER_AGENT} ^Go!Zilla [OR]RewriteCond %{HTTP_USER_AGENT} ^Go-Ahead-Got-It [OR]RewriteCond %{HTTP_USER_AGENT} ^GrabNet [OR]RewriteCond %{HTTP_USER_AGENT} ^Grafula [OR]RewriteCond %{HTTP_USER_AGENT} ^HMView [OR]RewriteCond %{HTTP_USER_AGENT} HTTrack [NC,OR]RewriteCond %{HTTP_USER_AGENT} ^Image\ Stripper [OR]RewriteCond %{HTTP_USER_AGENT} ^Image\ Sucker [OR]RewriteCond %{HTTP_USER_AGENT} Indy\ Library [NC,OR]RewriteCond %{HTTP_USER_AGENT} ^InterGET [OR]RewriteCond %{HTTP_USER_AGENT} ^Internet\ Ninja [OR]RewriteCond %{HTTP_USER_AGENT} ^JetCar [OR]RewriteCond %{HTTP_USER_AGENT} ^JOC\ Web\ Spider [OR]RewriteCond %{HTTP_USER_AGENT} ^larbin [OR]RewriteCond %{HTTP_USER_AGENT} ^LeechFTP [OR]RewriteCond %{HTTP_USER_AGENT} ^Mass\ Downloader [OR]RewriteCond %{HTTP_USER_AGENT} ^MIDown\ tool [OR]RewriteCond %{HTTP_USER_AGENT} ^Mister\ PiX [OR]RewriteCond %{HTTP_USER_AGENT} ^Navroad [OR]RewriteCond %{HTTP_USER_AGENT} ^NearSite [OR]RewriteCond %{HTTP_USER_AGENT} ^NetAnts [OR]RewriteCond %{HTTP_USER_AGENT} ^NetSpider [OR]RewriteCond %{HTTP_USER_AGENT} ^Net\ Vampire [OR]RewriteCond %{HTTP_USER_AGENT} ^NetZIP [OR]RewriteCond %{HTTP_USER_AGENT} ^Octopus [OR]RewriteCond %{HTTP_USER_AGENT} ^Offline\ Explorer [OR]RewriteCond %{HTTP_USER_AGENT} ^Offline\ Navigator [OR]RewriteCond %{HTTP_USER_AGENT} ^PageGrabber [OR]RewriteCond %{HTTP_USER_AGENT} ^Papa\ Foto [OR]RewriteCond %{HTTP_USER_AGENT} ^pavuk [OR]RewriteCond %{HTTP_USER_AGENT} ^pcBrowser [OR]RewriteCond %{HTTP_USER_AGENT} ^RealDownload [OR]RewriteCond %{HTTP_USER_AGENT} ^ReGet [OR]RewriteCond %{HTTP_USER_AGENT} ^SiteSnagger [OR]RewriteCond %{HTTP_USER_AGENT} ^SmartDownload [OR]RewriteCond %{HTTP_USER_AGENT} ^SuperBot [OR]RewriteCond %{HTTP_USER_AGENT} ^SuperHTTP [OR]RewriteCond %{HTTP_USER_AGENT} ^Surfbot [OR]RewriteCond %{HTTP_USER_AGENT} ^tAkeOut [OR]RewriteCond %{HTTP_USER_AGENT} ^Teleport\ Pro [OR]RewriteCond %{HTTP_USER_AGENT} ^VoidEYE [OR]RewriteCond %{HTTP_USER_AGENT} ^Web\ Image\ Collector [OR]RewriteCond %{HTTP_USER_AGENT} ^Web\ Sucker [OR]RewriteCond %{HTTP_USER_AGENT} ^WebAuto [OR]RewriteCond %{HTTP_USER_AGENT} ^WebCopier [OR]RewriteCond %{HTTP_USER_AGENT} ^WebFetch [OR]RewriteCond %{HTTP_USER_AGENT} ^WebGo\ IS [OR]RewriteCond %{HTTP_USER_AGENT} ^WebLeacher [OR]RewriteCond %{HTTP_USER_AGENT} ^WebReaper [OR]RewriteCond %{HTTP_USER_AGENT} ^WebSauger [OR]RewriteCond %{HTTP_USER_AGENT} ^Website\ eXtractor [OR]RewriteCond %{HTTP_USER_AGENT} ^Website\ Quester [OR]RewriteCond %{HTTP_USER_AGENT} ^WebStripper [OR]RewriteCond %{HTTP_USER_AGENT} ^WebWhacker [OR]RewriteCond %{HTTP_USER_AGENT} ^WebZIP [OR]RewriteCond %{HTTP_USER_AGENT} ^Widow [OR]RewriteCond %{HTTP_USER_AGENT} ^WWWOFFLE [OR]RewriteCond %{HTTP_USER_AGENT} ^Xaldon\ WebSpider [OR]RewriteCond %{HTTP_USER_AGENT} ^Zeus
```

#请注意黑名单列表的最后不要使用[OR]

#给以上列表的用户代理返回一个403错误（提示无权限访问）

```
RewriteRule .* - [F]
```

其他有用的设置

```
ServerSignature Off
```

#一般来说，Web服务器默认的只支持Post和Get这两种“只读”的请求方法。但是随着Ajax XMLHttpRequest 和 REST风格应用的深入，我们发现Http 1.1协议还支持如下请求方法（Request Method）：DELETE、OPTIONS、PUT、HEAD和TRACE，致使服务存在安全隐患。可以使用以下语句禁止

```
RewriteCond %{REQUEST_METHOD} ^(HEAD|TRACE|DELETE|TRACK) [NC,OR]
```

RewriteCond %{THE\_REQUEST} (\\r|\\n|%0A|%0D) [NC,OR]

RewriteCond %{HTTP\_REFERER} (<|>|’|%0A|%0D|%27|%3C|%3E|%00) [NC,OR]  
RewriteCond %{HTTP\_COOKIE} (<|>|’|%0A|%0D|%27|%3C|%3E|%00) [NC,OR]  
RewriteCond %{REQUEST\_URI} ^/(,|;|:|<|>|”>|”<|/|\\\.\.\\).{0,9999} [NC,OR]

RewriteCond %{HTTP\_USER\_AGENT} ^$ [OR]  
RewriteCond %{HTTP\_USER\_AGENT} ^(java|curl|wget) [NC,OR]  
RewriteCond %{HTTP\_USER\_AGENT} (winhttp|HTTrack|clshttp|archiver|loader|email|harvest|extract|grab|miner) [NC,OR]  
RewriteCond %{HTTP\_USER\_AGENT} (libwww-perl|curl|wget|python|nikto|scan) [NC,OR]  
RewriteCond %{HTTP\_USER\_AGENT} (<|>|’|%0A|%0D|%27|%3C|%3E|%00) [NC,OR]

#Block mySQL injects  
RewriteCond %{QUERY\_STRING} (;|<|>|’|”|\)|%0A|%0D|%22|%27|%3C|%3E|%00).\*(/\\*|union|select|insert|cast|set|declare|drop|update|md5|benchmark) [NC,OR]

RewriteCond %{QUERY\_STRING} \.\./\.\. [OR]

RewriteCond %{QUERY\_STRING} (localhost|loopback|127\.0\.0\.1) [NC,OR]  
RewriteCond %{QUERY\_STRING} \.[a-z0-9] [NC,OR]  
RewriteCond %{QUERY\_STRING} (<|>|’|%0A|%0D|%27|%3C|%3E|%00) [NC]  
# Note: The final RewriteCond must NOT use the [OR] flag.

# Return 403 Forbidden error.  
RewriteRule .\* index.php [F]

推荐的高阶htaccess文件

有关讨论可以在此页面找到：<http://forum.joomla.org/viewtopic.php?f=432&t=549841>  
注意：某些服务器设置不正确可能会引起500页面错误。

高阶 .htaccess

版本2.5（建议） - 2011年5月16日

```
＃这是一个.htaccess模板文件，你可以把它放置到你的网站来增加网站的安全和性能。但这并不意味着适用于你的网站。你需要修改此文件以符合你的网站需求，需要注意的是，你必须把文件中的example.com替换成你真实的域名。
```

#部分规则设置过于严格，可能导致合法的访问请求出现问题，你有责任注释它们或者添加例外规则。最值得注意的是，这些高级的规则会导致minifiers、eXtplorer、VirtueMart或其他一些使用非标准脚本入口的扩展出现问题，你必须手动添加他们的例外规则。

#某部分规则（取决于你的服务器配置）可能会导致你的网站出现500页面错误。唯一的解决方法是通过不断测试（注释）来找出哪部分规则导致错误。

#非常感谢Brian Teeman, Ken Crowder, Radek Suski and Fotis Evangelou分享他们的.htaccess规则和促进此文件的创建，特别感谢Jon Brown的分享他的研究与帮助改善此文件。

#还要感谢John的评论和g1smd抽空优化文件的处理速度。

#通常建议在实际使用中删除本文件的注释以提高文件的处理速度。

#你希望点几下鼠标就可以创建自己的定制.htaccess文件?AkeebaBackup.com的Admin Tools Professional可以满足你的需求，而且还有其他强大的功能。访问：<http://www.akeebabackup.com/software/admin-tools.html>

#玩得开心，注意安全。  
#Nicholas K. Dionysopoulos，AkeebaBackup.com的首席开发人员  
#  
#版本日志  
#2.5版（推荐）（2011年5月16日）  
#自定义代码中的点位符，修正排序规则。  
#2.4版（2011年4月18日）  
#数十处速度优化和许多逻辑和语法修正。  
#2.3版（2010年11月18日）  
#增加.ico通过规则来加载网站图标文件  
#2.2版（2010年10月25日）  
#修复tmpl=component 的bug  
#2.1版（2010年10月19日）  
# - 根目录重定向index.php会阻止一些AJAX的请求  
# - Referer的过滤问题  
# - 简化和更深入的处理"PHP 的復活節彩蛋"问题(感谢 Jon!)  
# - tp/template/tmpl过滤不彻底并阻隔某些组件  
# - 优化Joomla!核心的SEF功能  
# - Bot过滤器和GZip优化不会影响动态内容  
# - 内容过期的得到进一步优化  
# - 新增ETag规则

##########（开始）设置RewriteEngine启用  
RewriteEngine On  
##########（结束）设置RewriteEngine启用

##########（开始）设置RewriteBase  
#通常默认的虚拟主机的网站在使用.htaccess 进行重写规则时不需要执行设置该指令. 因为 RewriteBase 默认值是该 .htaccess 文件所在的目录地址。但是如果使用目录别名的话就需要设置这个指令。

# RewriteBase /  
##########（结束）设置RewriteBase

##########（开始）设置空目录文件列表显示  
#如果目录下没有index.\*文件，那么访问者就会看到当前目录的所有文件列表。使用IndexIgnore \*这样来访者会看到一个空的目录，什么文件都不会显示。Options +FollowSymLinks All -Indexes会给访问用户返回一个404错误。

IndexIgnore \*  
Options +FollowSymLinks All -Indexes  
##########（结束）设置空目录文件列表显示

##########（开始）设置默认文件执行次序  
DirectoryIndex index.php index.html  
##########（结束）设置默认文件执行次序

##########（开始）设置ETag的优化  
#此规则将会创建一个根据时间戳和文件大小而生成的ETag。如果你正在使用 rsync服务器，当文件完全相同而拥有不同的inode值，ETag是非常有用的。注意设置此规则可能导致网站出现500页面错误。（Etag 是URL的Entity Tag，用于标示URL对象是否改变，区分不同语言和Session等等。具体内部含义是使服务器控制的，就像Cookie那样。HTTP协议规格说明定义ETag为“被请求变量的实体值” 。另一种说法是，ETag是一个可以与Web资源关联的记号（token）。典型的Web资源可以一个Web页，但也可能是JSON或XML文档。服务器单独负责判断记号是什么及其含义，并在HTTP响应头中将其传送到客户端。）

FileETag MTime Size  
##########（结束）设置ETag的优化

##########（开始）设置封锁常见黑客工具和占用带宽的工具  
## 由 SigSiu.net 和 @nikosdion 提供。  
# 下行作用是禁止Akeeba 2.5或更早版本的远程控制。  
SetEnvIf user-agent "Indy Library" stayout=1  
# 警告：禁止wget将会影响CRON jobs（定时任务执行）的常规运行操作（如远程下载），如果你需要运行CRON jobs，请注释它  
SetEnvIf user-agent "Wget" stayout=1  
# 以下规则用于封锁一些占用带宽的下载工具  
SetEnvIf user-agent "libwww-perl" stayout=1  
SetEnvIf user-agent "Download Demon" stayout=1  
SetEnvIf user-agent "GetRight" stayout=1  
SetEnvIf user-agent "GetWeb!" stayout=1  
SetEnvIf user-agent "Go!Zilla" stayout=1  
SetEnvIf user-agent "Go-Ahead-Got-It" stayout=1  
SetEnvIf user-agent "GrabNet" stayout=1  
SetEnvIf user-agent "TurnitinBot" stayout=1  
# 下行会使上面设置的对象无法访问网站  
deny from env=stayout  
##########（结束）设置封锁常见黑客工具和占用带宽的工具

##########（开始）自动压缩资源   
# 压缩包括text、html、javascript、css、xml等资源（感谢Komra.de）  
# 可能会导致一些旧版本的IE浏览器无法访问你的网站。  
# 服务器需要有已编译的mod\_deflate模块，不然它会发送HTTP 500错误。  
# mod\_deflate不能用于Apache 1.x系列，只能用于Apache 2.x 的服务器。  
# AddOutputFilterByType用于旧模式的Apache，在新模式中mod\_filter过滤模块扩展了功能，允许过滤器根据有条件的规定运行。  
AddOutputFilterByType DEFLATE text/plain text/html text/xml text/css application/xml application/xhtml+xml application/rss+xml application/javascript application/x-javascript  
##########（结束）自动压缩资源

##########（开始）禁止恶意户代理或IP地址访问   
#如果你需要禁止某些恶意用户代理或者IP地址访问网站，可以在此处添加记录，使用RewriteRule命令和[F]标识  
#  
##########（结束）禁止恶意户代理或IP地址访问

##########（开始）使用重写规则来修复一些常见的漏洞  
#如果你的Joomla!网站遭遇以下常见类型的漏洞的攻击行为，你可以屏蔽掉它们。  
# 如果请求字符中包含 /proc/self/environ (by SigSiu.net)   
RewriteCond %{QUERY\_STRING} proc/self/environ [OR]  
# 阻止一些尝试通常URL来设置一个mosConfig的脚本 (这些攻击在Joomla! 1.5模式的插件中无法生效)  
RewriteCond %{QUERY\_STRING} mosConfig\_[a-zA-Z\_]{1,21}(=|\%3D) [OR]  
#阻止任何尝试把base64\_encode 或者base64\_decode数据添加到URL请求的脚本  
RewriteCond %{QUERY\_STRING} base64\_(en|de)code[^(]\*\([^)]\*\) [OR]  
#警告：如果上述的规则导致网站显示HTTP 500错误，请使用下面两行规则替换  
# RewriteCond %{QUERY\_STRING} base64\_encode\(.\*\) [OR]   
# RewriteCond %{QUERY\_STRING} base64\_decode\(.\*\) [OR]  
#阻止任何中带有<script>标签的URL请求  
RewriteCond %{QUERY\_STRING} (<|%3C)([^s]\*s)+cript.\*(>|%3E) [NC,OR]  
#阻止任何尝试把PHP全局变量添加到的URL请求的脚本  
RewriteCond %{QUERY\_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR]  
#阻止任何尝试把\_REQUEST变量添加到的URL请求的脚本   
RewriteCond %{QUERY\_STRING} \_REQUEST(=|\[|\%[0-9A-Z]{0,2})  
#返回一个403错误并转到主页  
RewriteRule .\* index.php [F]  
##########（结束）使用重写规则来修复一些常见的漏洞

##########（开始）文件注入保护  
RewriteCond %{REQUEST\_METHOD} GET   
RewriteCond %{QUERY\_STRING} [a-zA-Z0-9\_]=http:// [OR]  
RewriteCond %{QUERY\_STRING} [a-zA-Z0-9\_]=(\.\.//?)+ [OR]  
RewriteCond %{QUERY\_STRING} [a-zA-Z0-9\_]=/([a-z0-9\_.]//?)+ [NC]  
RewriteRule .\* - [F]  
##########（结束）文件注入保护

##########（开始）垃圾信息过滤  
#根据你的需要过滤掉一些常见词语，此代码使用PCRE和仅在Apache 2.x环境下生效，对Apache 1.x环境无效。  
RewriteCond %{QUERY\_STRING} \b(ambien|blue\spill|cialis|cocaine|ejaculation|erectile)\b [NC,OR]   
RewriteCond %{QUERY\_STRING} \b(erections|hoodia|huronriveracres|impotence|levitra|libido)\b [NC,OR]  
RewriteCond %{QUERY\_STRING} \b(lipitor|phentermin|pro[sz]ac|sandyauer|tramadol|troyhamby)\b [NC,OR]  
RewriteCond %{QUERY\_STRING} \b(ultram|unicauca|valium|viagra|vicodin|xanax|ypxaieo)\b [NC]  
## 注意：最近的规则不能使用[OR] 标识。  
RewriteRule .\* - [F]  
#上述的是过滤器的压缩版本，你也可以设置自己的过滤器，例如：RewriteCond %{QUERY\_STRING} \bbadword\b [NC,OR] ，你可以把需要过滤的词语填入此规则中"badword"的位置。  
##########（结束）垃圾信息过滤

##########（开始）高级服务器防护 - 查询字符串，索引和配置

#禁止PHP的复活节彩蛋（可以在使用指纹识别的攻击来确定您的PHP版本）。更多信息，请参阅<http://www.0php.com/php_easter_egg.php>和<http://osvdb.org/12184>  
RewriteCond %{QUERY\_STRING} \=PHP[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12} [NC] RewriteRule .\* - [F]

#SQLI的第一道防线，处理合法请求存在的一些问题  
RewriteCond %{QUERY\_STRING} concat[^\(]\*\( [NC,OR]   
RewriteCond %{QUERY\_STRING} union([^s]\*s)+elect [NC,OR]  
RewriteCond %{QUERY\_STRING} union([^a]\*a)+ll([^s]\*s)+elect [NC]  
RewriteRule .\* - [F]

#防盗链方法，禁止外部域名引用网站的媒体文件，同时有效地阻止常见的指纹识别攻击。注意，应把下面的www,example.com域名换成你的域名。  
RewriteRule ^images/stories/([^/]+/)\*([^/.]+\.)+(jp(e?g|2)?|png|gif|bmp|css|js|swf|ico)$ - [L]  
RewriteCond %{HTTP\_REFERER} .  
RewriteCond %{HTTP\_REFERER} !^https?://(www\.)?example\.com [NC]  
RewriteCond %{REQUEST\_FILENAME} -f  
RewriteRule \.(jp(e?g|2)?|png|gif|bmp|css|js|swf|ico)$ - [F]

#禁止Joomla网站的模板位置预览  
RewriteCond %{QUERY\_STRING} (^|&)tmpl=(component|system) [NC]   
RewriteRule .\* - [L]  
RewriteCond %{QUERY\_STRING} (^|&)t(p|emplate|mpl)= [NC]  
RewriteRule .\* - [F]

#禁止访问 htaccess.txt, configuration.php, configuration.php-dist and php.ini 文件   
RewriteRule ^(htaccess\.txt|configuration\.php(-dist)?|php\.ini)$ - [F]

##########（结束）高级服务器防护 - 查询字符串，索引和配置

##########（开始）添加高级服务器的例外规则  
## These are sample exceptions to the Advanced Server Protection 3.1 rule set further down this file.  
#允许 UddeIM CAPTCHA  
RewriteRule ^components/com\_uddeim/captcha15\.php$ - [L]  
## 允许 Phil Taylor's Turbo Gears  
RewriteRule ^plugins/system/GoogleGears/gears-manifest\.php$ - [L]  
## 允许 JoomlaWorks AllVideos  
RewriteRule ^plugins/content/jw\_allvideos/includes/jw\_allvideos\_scripts\.php$ - [L]  
## 允许 Admin Tools Joomla! updater to run  
RewriteRule ^administrator/components/com\_admintools/restore\.php$ - [L]  
## 允许Akeeba Backup Professional's integrated restoration script to run  
RewriteRule ^administrator/components/com\_akeeba/restore\.php$ - [L]  
## 允许 Akeeba Kickstart  
RewriteRule ^kickstart\.php$ - [L]

# 在这里为单独的php脚本添加更多规则

#允许Agora论坛的附件，但此目录的php脚本除外  
RewriteCond %{REQUEST\_FILENAME} !(\.php)$   
RewriteCond %{REQUEST\_FILENAME} -f  
RewriteRule ^components/com\_agora/img/members/ - [L]

# 在这里添加更多目录访问规则（php脚本除外）

##取消注释，允许完全访问缓存目录（强烈不推荐）   
#RewriteRule ^cache/ - [L]  
## 取消注释，允许完全访问临时目录（强烈不推荐）  
#RewriteRule ^tmp/ - [L]

# 在这里添加更多访问规划

##########（结束）添加高级服务器的例外规则

##########（开始）高级服务器保护 - 路径与文件

## 后台保护  
##这通常禁止通过指纹攻击来浏览XML和INI文件  
RewriteRule ^administrator/?$ - [L]  
RewriteRule ^administrator/index\.(php|html?)$ - [L]  
RewriteRule ^administrator/index[23]\.php$ - [L]  
RewriteRule ^administrator/(components|modules|templates|images|plugins)/([^/]+/)\*([^/.]+\.)+(jp(e?g|2)?|png|gif|bmp|css|js|swf|html?|mp(eg?|[34])|avi|wav|og[gv]|xlsx?|docx?|pptx?|zip|rar|pdf|xps|txt|7z|svg|od[tsp]|flv|mov)$ - [L]  
RewriteRule ^administrator/ - [F]

## 明确只允许访问XML-RPC的xmlrpc/index.php 文件或者xmlrpc/ 目录   
RewriteRule ^xmlrpc/(index\.php)?$ - [L]  
RewriteRule ^xmlrpc/ - [F]

## 禁止由前端访问Joomla!的系统目录  
RewriteRule ^includes/js/ - [L]  
RewriteRule ^(cache|includes|language|libraries|logs|tmp)/ - [F]

##允许客户端在一定范围内访问joomla!的系统目录   
RewriteRule ^(components|modules|plugins|templates)/([^/]+/)\*([^/.]+\.)+(jp(e?g|2)?|png|gif|bmp|css|js|swf|html?|mp(eg?|[34])|avi|wav|og[gv]|xlsx?|docx?|pptx?|zip|rar|pdf|xps|txt|7z|svg|od[tsp]|flv|mov)$ - [L]  
## 取消注释，假如你需要直接访问你的扩展的定制index.php文件，但请注意，这是不安全的，开发者应该为自己的拙劣、懒惰、毫无安全意识而感到羞耻  
# RewriteRule ^(components|modules|plugins|templates)/([^/]+/)\*(index\.php)?$ - [L]  
## 取消注释，假如你的模板需要直接访问其目录内的php脚本，如gzip压缩的CSS文件的副本  
# RewriteRule ^templates/([^/]+/)\*([^/.]+\.)+php$ - [L]  
RewriteRule ^(components|modules|plugins|templates)/ - [F]

## 不允许恶意php脚本访问整个网站，除非它们被明确允许   
RewriteCond %{REQUEST\_FILENAME} \.php$  
RewriteCond %{REQUEST\_FILENAME} !/index[23]?\.php$  
## 下行明确允许论坛帖子助手(fpa-xx)脚本运行  
RewriteCond %{REQUEST\_FILENAME} !/fpa-[a-z]{2}\.php  
RewriteCond %{REQUEST\_FILENAME} -f  
RewriteRule ^([^/]+/)\*([^/.]+\.)+php$ - [F]

##########（结束）高级服务器保护 - 路径与文件

##########（开始）Google Apps 重定向   
## 取消注释，使下行内容生效  
# RewriteRule ^mail <http://mail.google.com/a/example.com> [R=301,L]  
## 如果取消上行注释并不能生效，可以尝试下行  
## RewriteRule ^mail <http://mail.google.com/a/example.com> [R,L]  
##########（结束）Google Apps 重定向

##########（开始）自定义重定向   
#如果你需要重定向一些页面，请在下面添加代码，确保这些重定向使用了正确的RewriteRule语法和 [R=301,L]标识##########（结束）自定义重定向

##########（开始）重定向旧的域名(www.)olddomain.com到新域名www.example.com   
## 注意： olddomain.com是指你的旧域名，而www.example.com 是你希望重定向到的新域名。  
##把以上域名替换成你实际的名称，注意，这部分语句应该放置在旧域名的配置文件中(除非新旧域名挂载同一个空间)  
## 注意：如果你的网站显示500错误，请使用[R,L]替换[R=301,L]  
## 取消注释，使下面语句生效：  
# RewriteCond %{HTTP\_HOST} ^(www\.)?olddomain\.com [NC]  
# RewriteRule (.\*) <http://www.example.com/$1> [R=301,L]  
## 注意：以上部分仅替换成你的实际域名即可。  
##########（结束）重定向旧的域名(www.)olddomain.com到新域名www.example.com

##########（开始）强制某些页面以HTTPS模式运行  
# 强制某些页面以HTTPS模式运行，而不管Joomla!是如何设置。  
# 这是以foobar.html页面为例，记住把www.example.com 替换成你的域名。你需要为每个指定的页面添加一条规则。  
RewriteCond %{SERVER\_PORT} !^443$  
##另外，注释上行和取消下行注释   
# RewriteCond %{HTTPS} ^off$ [NC]  
RewriteRule ^foobar\.html$ <https://www.example.com/foobar.html> [R=301,L]  
## 注意：如果你的网站显示HTTP 500 错误，请把 [R=301,L]替换成 [R,L]  
# 根据需要，在下行添加更多规则  
##########（结束）强制某些页面以HTTPS模式运行

##########（开始）重定向index.php到 /    
## 注意：把example.com替换成你的域名  
RewriteCond %{THE\_REQUEST} !^POST  
RewriteCond %{THE\_REQUEST} ^[A-Z]{3,9}\ /index\.php\ HTTP/  
RewriteCond %{SERVER\_PORT}>s ^(443>(s)|[0-9]+>s)$  
RewriteRule ^index\.php$ http%2://www.example.com/$1 [R=301,L]  
## 注意：如果你的网站显示500错误，请使用[R,L]替换[R=301,L]  
##########（结束）重定向index.php到 /

##########（开始）重定向无www的域名到带www的域名  
#对于[joomla建站](http://www.ycway.com/joomla-web-design)来说，这个是经常使用到的   
RewriteCond %{HTTP\_HOST} !^www\. [NC]  
RewriteRule ^(.\*)$ <http://www.%{HTTP_HOST}/$1> [R=301,L]  
## 注意：如果你的网站显示500错误，请使用[R,L]替换[R=301,L]  
##########（结束）重定向无www的域名到带www的域名

##########（开始）重定向带www的域名到无www的域名   
## 警告，请先注释掉上面的规则，然后取消注释下面的规则，使其生效  
# RewriteCond %{HTTP\_HOST} ^www\.(.+)$ [NC]  
# RewriteRule ^(.\*)$ <http://%1/$1> [R=301,L]  
## 注意：如果你的网站显示500错误，请使用[R,L]替换[R=301,L]  
##########（结束）重定向带www的域名到无www的域名

##########（开始）定制的内部重写  
##如果你需要一些特定的URL请求，请在下面添加规则。确保每条规则使用了正确的RewriteRule语法和[L]标识，并不带有域名。  
##########（结束）定制的内部重写

##########（开始）Joomla!核心SEF部分  
RewriteRule .\* - [E=HTTP\_AUTHORIZATION:%{HTTP:Authorization}]  
# 如果请求的路径和文件不是/ index.php并且请求已​​在内部重写到index.php脚本  
RewriteCond %{REQUEST\_URI} !^/index\.php  
#站点根目录的请求，或作为扩展名的URL，或URL请求以某一扩展名结束  
RewriteCond %{REQUEST\_URI} /component/|(/[^.]\*|\.(php|html?|feed|pdf|vcf|raw|ini|zip|json|file))$ [NC]  
#请求的路径和文件不直接匹配的物理文件  
RewriteCond %{REQUEST\_FILENAME} !-f  
# 请求的路径不直接匹配的物理文件夹  
RewriteCond %{REQUEST\_FILENAME} !-d  
# 内部重写请求去掉index.php脚本  
RewriteRule .\* index.php [L]  
##########（结束）Joomla!核心SEF部分

##########（开始）优化默认的过期时间  
########## Begin - Optimal default expiration time   
## 注意：这可能会引发问题，你需要通过在此前一行放置一个hash来注释它  
<IfModule mod\_expires.c>  
# 启用过期控制  
ExpiresActive On

# 默认过期时间：请求后1小时  
ExpiresDefault "now plus 1 hour"

# CSS和JS文件过期时间：请求后1周  
ExpiresByType text/css "now plus 1 week"  
ExpiresByType application/javascript "now plus 1 week"  
ExpiresByType application/x-javascript "now plus 1 week"

# 图像文件过期时间：请求后1个月  
ExpiresByType image/bmp "now plus 1 month"  
ExpiresByType image/gif "now plus 1 month"  
ExpiresByType image/jpeg "now plus 1 month"  
ExpiresByType image/jp2 "now plus 1 month"  
ExpiresByType image/pipeg "now plus 1 month"  
ExpiresByType image/png "now plus 1 month"  
ExpiresByType image/svg+xml "now plus 1 month"  
ExpiresByType image/tiff "now plus 1 month"  
ExpiresByType image/vnd.microsoft.icon "now plus 1 month"  
ExpiresByType image/x-icon "now plus 1 month"  
ExpiresByType image/ico "now plus 1 month"  
ExpiresByType image/icon "now plus 1 month"  
ExpiresByType text/ico "now plus 1 month"  
ExpiresByType application/ico "now plus 1 month"  
ExpiresByType image/vnd.wap.wbmp "now plus 1 month"  
ExpiresByType application/vnd.wap.wbxml "now plus 1 month"  
ExpiresByType application/smil "now plus 1 month"

# 音频文件过期时间：请求后1个月  
ExpiresByType audio/basic "now plus 1 month"  
ExpiresByType audio/mid "now plus 1 month"  
ExpiresByType audio/midi "now plus 1 month"  
ExpiresByType audio/mpeg "now plus 1 month"  
ExpiresByType audio/x-aiff "now plus 1 month"  
ExpiresByType audio/x-mpegurl "now plus 1 month"  
ExpiresByType audio/x-pn-realaudio "now plus 1 month"  
ExpiresByType audio/x-wav "now plus 1 month"

# 视频文件过期时间：请求后1个月  
ExpiresByType application/x-shockwave-flash "now plus 1 month"  
ExpiresByType x-world/x-vrml "now plus 1 month"  
ExpiresByType video/x-msvideo "now plus 1 month"  
ExpiresByType video/mpeg "now plus 1 month"  
ExpiresByType video/mp4 "now plus 1 month"  
ExpiresByType video/quicktime "now plus 1 month"  
ExpiresByType video/x-la-asf "now plus 1 month"  
ExpiresByType video/x-ms-asf "now plus 1 month"  
</IfModule>  
##########（结束）优化默认的过期时间

文章來自：[Joomla的htaccess文件使用范例](http://www.ycway.com/joomla/joomla-htaccess.html)

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [Joomla的htaccess文件使用范例](http://www.joomla178.com/joomla-share/research-and-development/how-to-use-joomla-htaccess.html)
