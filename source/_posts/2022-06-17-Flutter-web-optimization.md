---
title: Flutter Web 优化方案
date: 2022-06-17 17:28:28
tags: flutter
---

主要是 main.dart.js 和 字体。参考文章

https://blog.csdn.net/ZuoYueLiang/article/details/124651244

https://juejin.cn/post/7095294020900880420#heading-4

#### 美团的解决方案

https://tech.meituan.com/2021/12/16/flutterweb-practice-in-meituan-waimai.html

在没有达到美团优化的高度时，服务器开启 gzip 是很有必要的。

不是很懂web，不知道怎么拆分 js,不过服务器开启压缩以后，main.dart.js 大概 400kb 左右。

关于服务器如何开启 gzip https://juejin.cn/post/6844903602822070280
