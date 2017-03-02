---
title: Git笔记
date: 2016-5-26 22:34:41
tags:
- 编程
- VCS
categories: 编程
---
# 设置远程仓库
`git remote add origin git@github.com:vcnovember/hexo-theme-next.git`

# 同时管理多个仓库
利用ssh config

<!-- more -->
# 删除远程分支
+ `git push origin --delete master`
+ `git push  origin:master`
# 同步 Github fork 出来的分支
+ [如何同步 Github fork 出来的分支](http://jinlong.github.io/2015/10/12/syncing-a-fork/)
+ [Github官方指南](https://help.github.com/articles/configuring-a-remote-for-a-fork/)