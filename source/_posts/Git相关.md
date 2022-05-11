---
title: Git 相关
categories: iOS开发
---



### Git 分支规范

#### 主分支 master

- master 为主分支，要保护它的稳定性，随时可以用来上线。
- 我们不应该直接在master 分支上直接提交代码，而是从其他分支的合并。

#### 开发分支 develop

- develop 为开发分支，一般包含正在开发的所有新特性，用于测试环境部署和测试。
- 我们不应该直接在develop 分支上直接提交代码，也不应该把未经测试的代码合并进来，应该尽量保持测试环境干净可用。
- 当 develop 太 “脏”以至于不能继续测试之后，可以考虑重新从 master 拉取一次。

#### 性能分支 feature

- 分支命名：feature/ 开头的为特性分支，命名规则为 feature/some_amazing_funs-yourname-date。举例，如钱米1月31号要开发一个通讯录改进的功能，可以自建分支为feature/contacts_advance-qm-0131。
- 一般 feature 分支应仅包含一个特性，上线（合并至master）部署验证无误后即可删除。记得及时将 feature 分支 push 至远端。
- 如果合并至 develop 或 master 时发现在 fork 此特性分支之后分支已合并了很多其他分支的提交，请先执行 git rebase，这样能提交历史更加整洁。

#### 预上线分支 release 

- 分支命名：release/ 开头的为预发布分支，命名规则为 release/date。举例来讲，如果1月31号要准备封一个预上线分支，则命名为 release/0131。
- 上线后即可删除。

#### 快速修复分支 hotfix

- 分支命名：hotfix/开头的为修复分支，它的命名规则与feature 分支类似。
- 一般我们如果发现紧急线上bug，可以将线上代码临时回滚，从最新的 master 分支建立 hotfix 分支，提交修复代码、测试无误后，合并至 develop 和 master 。
- 上线验证无误后，即可将 hotfix 分支删除。



### Git 常用命令

#### 本地创建远程分支

```
git checkout -b develop
git push origin develop:develop //冒号前develop 为远程分支名，后面为本地分支名称。	
```

#### 删除远程分支

```
git push origin :develop //推送一个空的分支到远程分支，其实就相当于删除远程分支
git push origin —delete develop //直接删除分支	
```

### 合并分支

```
git merge develop
//当前分支去合并 develop 分支的内容和 develop 保持一致
```



### 添加.gitignore 文件

​	[简书链接](https://www.jianshu.com/p/a09a9b40ad20)



