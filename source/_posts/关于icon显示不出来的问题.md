---
title: 关于不显示 icon 的问题
---



### 关于icon显示不出来的问题

主要还是因为cocoapods，还要就是iPad要添加图片 只需要添加如下三个尺寸就好了。

![](https://ws2.sinaimg.cn/large/006tKfTcgy1fs7a3m9047j312a0wwq8e.jpg)

还需要在这个文件夹路径下添加东西路径如下：

这是我项目的路径/SecretPhoto/Pods/Target\ Support\ Files/Pods-SecretPhoto/Pods-SecretPhoto-resources.sh 

![](https://ws1.sinaimg.cn/large/006tKfTcgy1fs797kqld8j31bu0b4n1r.jpg)

在这个文件夹下最下面添加如下代码

```
--app-icon "${ASSETCATALOG_COMPILER_APPICON_NAME}" --output-partial-info-plist "${BUILD_DIR}/assetcatalog_generated_info.plist"
```

添加后如下

![](https://ws1.sinaimg.cn/large/006tKfTcgy1fs7a6iycc9j31by08uju2.jpg)

解决问题。

***还有就是不要用xCode Beat 版本跑，不然还是不显示***

我用的xCode10 beat 版跑真机iPhone X不显示，用xCode9.4稳定版，显示。