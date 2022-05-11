---
title: 嵌套加载 RN 界面
---

### 修改说明

1.把 RN 文件夹里面的文件替换掉 BaseShell-develop 里面的文件 包括以下四个文		件,全部替换，然后 npm install 加载依赖

![](https://ws1.sinaimg.cn/large/006tKfTcgy1fsjxnxyyokj30mu05iwf0.jpg)

2.把 Native 整个文件全都拖拽到 iOS 项目中，配置 pch 文件路径 文件目录如下：

![](https://ws2.sinaimg.cn/large/006tKfTcgy1fsjxfmqr2ij30eu0se0ws.jpg)

3.因为我的这个 私密相册 用到了cocoapods ，所以把 Podfile 文件拷贝到 iOS 项目目录下，运行 pod install ，然后重新打开 iOS 项目

4.用我写的测试项目，还需要把图片资源添加到 Image.xcassets 中 在文件夹中的 PicResource

5.开发完壳的 RN 代码后需要打包能本地加载的 jsbundle , 打包命令如下

```
react-native bundle --entry-file ./index.js --bundle-output ./ios/bundle/rn.jsbundle --platform ios --assets-dest ./ios/bundle --dev false

参数说明：
--entry-file 指定入口文件 因为要打包ios平台，所以指定为rn项目的index.js作为入口
--bundle-output 指定输出的jsbundle文件路径和文件名 指定到rn项目的ios工程文件夹下，记得一定要先创建bundle文件夹，不然终端会报文件夹找不到的错误
--platform 指定平台类型
--assets-dest 指定资源文件夹路径 assets文件夹的路径，包含图片、node模块等资源
--dev 是否为开发模式 如果设置为false，不会产生警告，并且bundle会被压缩
还有其他命令，比如：transformer、prepack、bundle-encoding等，可以到官网查看具体介绍。
```

打包完以后需要把 bundle 文件夹添加到工程项目中 然后测试加载本地 jsbundle 如果没有问题就可以 Archive 发包了。

注意：如果运行完 pod install icon 加载不出来，参考我的这个博客 [博客地址](https://captain91.github.io/2018/06/11/关于icon显示不出来的问题/)

