# 一  查看git配置的信息

* `git config  --list ` 


# 二  添加远程仓库

`git remote add origin https://github.com/bigDataHell/blog_angular`

* origin : url的简写
* https://github.com/bigDataHell/blog_angular : 远程仓库地址

# 三  git推送到远程仓库

## 3.1 推送到主分支

* `git push orgin master`

# 四 git远程仓库拉取

# 五 分支操作

## 5.1 分支创建

* 创建testing分支:  `git branch testing`
* 创建testing分支并且换到testing分支:  `git branch -b testing`

## 5.2 查看各个分支当前所指的对象
* `git log --oneline --decorate`

* 查看当前所在的分支: `git branch`

## 5.3 分支切换

* `git checkout testing`

## 5.4 查看分叉历史
* `git log --oneline --decorate --graph --all`

## 5.5 把新创建的分支推送到远端

* 远端会自动创建名为:`blog_angular_test`的分支
* `git push origin blog_angular_test`

## 5.5本地分支跟踪远端分支

* `git branch --set-upstream-to=origin/blog_angular_test blog_angular_test`

## 5.6 查看分支关联的远程分支

* `git branch -vv`

## 5.7 拉去远程分支

* `git pull`

## 5.8 推送远程分支

* `git push`
