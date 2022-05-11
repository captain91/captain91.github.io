---
title: Unity 集成到原生相关
categories: iOS开发
---



### unity 集成到 iOS 原生

[官网链接](https://github.com/Unity-Technologies/uaal-example/blob/master/docs/ios.md)

[如何将Unity以库形式集成到原生iOS和Android应用](https://blog.csdn.net/CSDN_ONION/article/details/104069499)

[iOS原生集成unity—framework形式集成](https://www.jianshu.com/p/f919cb90821e)



### ***最后精简为

把 UnityFramework.framework 添加到项目中，把打包出来的游戏文件夹 Data 引入项目；

配置启动即可加载， 配置启动方法，官网给出的原生加载方式，NativeiOSApp 项目里查看

### 理解为游戏引擎 + 游戏资源

![](https://tva1.sinaimg.cn/large/008eGmZEgy1goew80nsmej30e00jk3zz.jpg)



### 资源 Data

1.可以直接集成到 Unityframework.framework 中，需要使用以下加载方法

```objective-c
[[self ufw] setDataBundleId: "com.unity3d.framework"];
```

2.直接放到项目中，可用以下两种加载方式

```objective-c
id ufw = UnityFrameworkLoad();
[ufw runUIApplicationMainWithArgc: argc argv: argv];
or
[ufw runEmbeddedWithArgc: argc argv: argv appLaunchOpts:launchOptions];
```

