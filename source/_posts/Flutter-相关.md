---
title: Flutter 相关
categories: iOS开发
---

### 原生集成 flutter 打包上传

1.看官方网站的集成方式比较新和全 [官网链接](https://flutter.dev/docs/development/add-to-app/ios/project-setup)

​	看推荐的 Option A 就可以 以下操作是在 Option A 的基础上

2.打包发布的时候需要在 my_flutter 文件路径下运行以下命令

```
flutter build ios --release --no-codesign
```

3.然后直接走 Xcode Archive流程



### 其他方案

[Flutter - 将 Flutter 集成到现有项目（iOS - Framework篇）](https://blog.csdn.net/qq_23756803/article/details/106678410)

