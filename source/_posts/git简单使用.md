---
title: Git 常用命令
date: 2019-11-04 10:36:16
tags: git
---

###  [git 分支的管理策略](https://www.ruanyifeng.com/blog/2012/07/git.html)

### 把本地的分支替换成远程的分支，强制替换

```
git fetch --all
git rest --hard origin/master （这里的 master 要修改为对应的分支名）
git pull
```



### 查看本地分支与远程分支的映射关系

```
git branch -vv
```



### 建立本地分支与远程分支的映射关系

```
git remote add origin 仓库地址
git branch -u origin/master (此处为远程分支名)
或者用一下命令
git branch --set-upstream-to origin/master (同上)

建立关系以后 git pull 就会成功把远程拉到本地，或 git push 推送到远程分支
```



### 撤销本地分支与远程分支的映射关系

```
git branch --unset-upstream
```



### 更新远程分支

```
git remote update origin --prune
```



### 删除本地和远程分支

```
删除本地分支
git branch -d <BranchName>

删除远程分支
git push origin --delete <BranchName>

```



###  保存和恢复进度 	[详细点击](https://blog.csdn.net/daguanjia11/article/details/73810577)

```
保存当前工作进度,运行后可以切换分支
git stash

显示保存进度的列表
git stash list

恢复最新的进度到工作区
git stash pop
```



### git还原到之前某个版本，本地和远程都还原

```
git log 查看之前的commit的id，找到想要还原的版本
git reset --hard 44bd896bb726be3d3815f1f25d738a9cd402a477   还原到之前的某个版本
git push -f origin master  强制push到远程
```



#### git 更换仓库地址

```
git remote set-url origin git@example.com/username/newproject.git

还有一个简单粗暴的，直接找到 .git 打开 config 修改 url
```



#### 忽略本地修改

```
git update-index --skip-worktree /path/to/file
```



#### 删除已经添加 add 的文件

```
git rm --cached "文件路径"
```

#### 只获取远程指定分支

```
git clone -b source git@github.com:xxxxx/xxxxx.git
```

