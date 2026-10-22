---
title: "提取自Framework7的userAgent插件，用于监听设备浏览器型号"
source: "http://www.joomla178.com/joomla-share/front-end/get-from-framework7-useragent-plugin.html"
category: "前端开发"
author: "Jiang"
date: "2016-01-08"
archived_at: "2026-10-22T11:56:29.930671+08:00"
---

# 提取自Framework7的userAgent插件，用于监听设备浏览器型号

最近工作重点在基于nodejs前端开发环境中，前端框架挑选不在少数，移动端框架选用了Framework7之后在其中学习了不少先进理念，今天分享一下F7当中的设备监听插件提取及应用在jquery中。本人采用grunt开发环境编译js和css，所以grunt环境的配置编译不作介绍，自行爬教程。

插件主要作用是在html或者body中增加样式选择器，生效之后效果如下：

```
<body class="pixel-ratio-3 retina ios ios-8 ios-8-0 ios-gt-7 ios-gt-6">
...
</body>
```

再通过样式去控件各种设备需要的UI

在F7的项目目录中找到/src/js/proto-device.js文件，只需将其$声明改掉即可兼容jquery或者bootstrap。

### jQuery插件

移除其中的$符声明，转换成jquery插件方式表现，代码如下：

```
(function($){
    $.fn.useragt = function(options){
        return this.each(function(){
            var device = {};
            var ua = navigator.userAgent;

            var android = ua.match(/(Android);?[\s\/]+([\d.]+)?/);
            var ipad = ua.match(/(iPad).*OS\s([\d_]+)/);
            var ipod = ua.match(/(iPod)(.*OS\s([\d_]+))?/);
            var iphone = !ipad && ua.match(/(iPhone\sOS)\s([\d_]+)/);

            device.ios = device.android = device.iphone = device.ipad = device.androidChrome = false;

            // Android
            if (android) {
                device.os = 'android';
                device.osVersion = android[2];
                device.android = true;
                device.androidChrome = ua.toLowerCase().indexOf('chrome') >= 0;
            }
            if (ipad || iphone || ipod) {
                device.os = 'ios';
                device.ios = true;
            }
            // iOS
            if (iphone && !ipod) {
                device.osVersion = iphone[2].replace(/_/g, '.');
                device.iphone = true;
            }
            if (ipad) {
                device.osVersion = ipad[2].replace(/_/g, '.');
                device.ipad = true;
            }
            if (ipod) {
                device.osVersion = ipod[3] ? ipod[3].replace(/_/g, '.') : null;
                device.iphone = true;
            }
            // iOS 8+ changed UA
            if (device.ios && device.osVersion && ua.indexOf('Version/') >= 0) {
                if (device.osVersion.split('.')[0] === '10') {
                    device.osVersion = ua.toLowerCase().split('version/')[1].split(' ')[0];
                }
            }

            // Webview
            device.webView = (iphone || ipad || ipod) && ua.match(/.*AppleWebKit(?!.*Safari)/i);
                
            // Minimal UI
            if (device.os && device.os === 'ios') {
                var osVersionArr = device.osVersion.split('.');
                device.minimalUi = !device.webView &&
                                    (ipod || iphone) &&
                                    (osVersionArr[0] * 1 === 7 ? osVersionArr[1] * 1 >= 1 : osVersionArr[0] * 1 > 7) &&
                                    $('meta[name="viewport"]').length > 0 && $('meta[name="viewport"]').attr('content').indexOf('minimal-ui') >= 0;
            }

            // Classes
            var classNames = [];

            // Pixel Ratio
            device.pixelRatio = window.devicePixelRatio || 1;
            classNames.push('pixel-ratio-' + Math.floor(device.pixelRatio));
            if (device.pixelRatio >= 2) {
                classNames.push('retina');
            }

            // OS classes
            if (device.os) {
                classNames.push(device.os, device.os + '-' + device.osVersion.split('.')[0], device.os + '-' + device.osVersion.replace(/\./g, '-'));
                if (device.os === 'ios') {
                    var major = parseInt(device.osVersion.split('.')[0], 10);
                    for (var i = major - 1; i >= 6; i--) {
                        classNames.push('ios-gt-' + i);
                    }
                }
            }

            // Add html classes
            if (classNames.length > 0) $(this).addClass(classNames.join(' '));

            // Export object
            return device;
        });
    };
})(jQuery);
```

在页面中使用方法，也可以换成$("html")：

```
$(function(){
    $("body").useragt();
});
```

### Bootstrap

Bootstrap主要是编译合并，所以修改如下即可（默认是来标识样式选择器）：

```
+function ($) {
    'use strict';
    var device = {};
    var ua = navigator.userAgent;

    var android = ua.match(/(Android);?[\s\/]+([\d.]+)?/);
    var ipad = ua.match(/(iPad).*OS\s([\d_]+)/);
    var ipod = ua.match(/(iPod)(.*OS\s([\d_]+))?/);
    var iphone = !ipad && ua.match(/(iPhone\sOS)\s([\d_]+)/);

    device.ios = device.android = device.iphone = device.ipad = device.androidChrome = false;

    // Android
    if (android) {
        device.os = 'android';
        device.osVersion = android[2];
        device.android = true;
        device.androidChrome = ua.toLowerCase().indexOf('chrome') >= 0;
    }
    if (ipad || iphone || ipod) {
        device.os = 'ios';
        device.ios = true;
    }
    // iOS
    if (iphone && !ipod) {
        device.osVersion = iphone[2].replace(/_/g, '.');
        device.iphone = true;
    }
    if (ipad) {
        device.osVersion = ipad[2].replace(/_/g, '.');
        device.ipad = true;
    }
    if (ipod) {
        device.osVersion = ipod[3] ? ipod[3].replace(/_/g, '.') : null;
        device.iphone = true;
    }
    // iOS 8+ changed UA
    if (device.ios && device.osVersion && ua.indexOf('Version/') >= 0) {
        if (device.osVersion.split('.')[0] === '10') {
            device.osVersion = ua.toLowerCase().split('version/')[1].split(' ')[0];
        }
    }

    // Webview
    device.webView = (iphone || ipad || ipod) && ua.match(/.*AppleWebKit(?!.*Safari)/i);
        
    // Minimal UI
    if (device.os && device.os === 'ios') {
        var osVersionArr = device.osVersion.split('.');
        device.minimalUi = !device.webView &&
                            (ipod || iphone) &&
                            (osVersionArr[0] * 1 === 7 ? osVersionArr[1] * 1 >= 1 : osVersionArr[0] * 1 > 7) &&
                            $('meta[name="viewport"]').length > 0 && $('meta[name="viewport"]').attr('content').indexOf('minimal-ui') >= 0;
    }

    // Classes
    var classNames = [];

    // Pixel Ratio
    device.pixelRatio = window.devicePixelRatio || 1;
    classNames.push('pixel-ratio-' + Math.floor(device.pixelRatio));
    if (device.pixelRatio >= 2) {
        classNames.push('retina');
    }

    // OS classes
    if (device.os) {
        classNames.push(device.os, device.os + '-' + device.osVersion.split('.')[0], device.os + '-' + device.osVersion.replace(/\./g, '-'));
        if (device.os === 'ios') {
            var major = parseInt(device.osVersion.split('.')[0], 10);
            for (var i = major - 1; i >= 6; i--) {
                classNames.push('ios-gt-' + i);
            }
        }        
    }
    
    // Add html classes
    if (classNames.length > 0) $('html').addClass(classNames.join(' ')); //样式选择器可以设置为body

    // Export object
    return device;
}(jQuery);
```

---

除特殊标明文章转自第三方网站，文章均由JOOMLASK.COM原创提供  
欢迎友情转载，请务必保留本文出处并引用本文链接： [提取自Framework7的userAgent插件，用于监听设备浏览器型号](http://www.joomla178.com/joomla-share/front-end/get-from-framework7-useragent-plugin.html)
