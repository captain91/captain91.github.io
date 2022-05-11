---
title: 创建 cocoapods 文件
---

### 添加到 cocoapods 

- 创建 GitHub 仓库 记得勾选 Add  a license 选 MIT License 

  [具体请看](https://www.kancloud.cn/thinkphp/github-tips/37890)

  ![](https://ws2.sinaimg.cn/large/006tKfTcgy1ft80po0pigj30go08a0tq.jpg)

- 推送到远程仓库

  ```
  git add .
  git commit -m 'First commit'
  git push -u origin master
  ```

- 添加标签

  ```
  git tag 0.0.1
  git tag
  git push --tags
  ```

- 添加并填写 podspec 文件

  ```
  pod spec create xxxxx   (工程名字)
  ```

  修改 xxxxx.podspec  项目目录下要添加一个 LICENSE 文件

  ```
   s.name         = "xxxxx"
   s.version      = "0.0.1"
   s.summary      = "Test BSWebImage."
   s.homepage     = "https://github.com/captain91/xxxxx.git"
   s.license      = { :type => "MIT", :file => "LICENSE" }
   s.author             = { "Shibo Sun" => "cxxxxxxxx@163.com" }
   s.platform     = :ios, "9.0"
   s.source       = { :git => "https://github.com/captain91/xxxxx.git", :tag => "#{s.version}" }
   s.source_files  = "ShareToCocoapods/**" (要被共享的文件路径)
   s.requires_arc = true
  ```

- 保存podspec文件，然后验证，如果通过会有如下信息，如果没有通过，查看之前的步骤是否有错误。需要注意的点

  <table> <td bgcolor=DarkGray> 

  1.远程仓库是否有tag值，tag值是否和本地的tag值相等

  2.podspec信息是否填写正确 

  3.本地库的东西是否推送到远程仓库

  </td></table>

  ```
  pod lib lint (碰到问题解决问，尽量不要有警告)
  ```

- 注册 trunk  然后去邮箱验证

  ```
  pod trunk register cxxxxxxxx@163.com 'cocoapods test' --description='cocoapods test'
  ```

- 上传 

  ```
  pod trunk push xxxxx.podspec
  ```

- 更新本地仓库 （上传理想的情况下，有问题去 Google）

  ```
  pod repo update
  ```

  这个时候，就pod search 一下你的工程。如果没有，就把~/Library/Caches/CocoaPods这里面的search_index.json文件删了再重新搜

- 删除 pods 

  ```
  pod trunk delete XLGCategory 1.0.0  #删除指定版本的pods
  pod trunk deprecate XLGCategory #将pods设置为过期
  ```

  

### GitHub 上传超过 100M 的大文件

[链接](https://www.jianshu.com/p/3f25cd20e392)

取你所需要的。