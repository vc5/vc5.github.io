---
layout: drafts
title: 使用 git submodule管理hexo主体
date: 2020-3-14 17:24:56
tags:
---
#  基本使用
现在我们使用 Git submodules 的方式来选择一个第三方主题来替换原本的 landscape 主题. 这里选择我比较喜欢的的 pure 主题.
`git submodule add https://github.com/cofess/hexo-theme-pure themes/pure`
git 便会将 hexo-theme-pure 主题作为一个项目子模块 clone 到 themes/pure 中. 同时 hexo 项目中会自动生成一个 .gitmodules 文件, 这个配置文件中保存了项目 URL 与已经拉取的本地目录之间的映射.
## .gitmodules 文件内容
```
$ cat .gitmodules
[submodule "themes/pure"]
	path = themes/pure
	url = https://github.com/cofess/hexo-theme-pure
```

# 更新主题
主题作为子模块添加到项目中后, 若主题作者有更新, 便可通过两种方法来拉取主题的更新内容.
  1. 进入themes 下主题目录, 执行 `git fetch `和 `git merge origin/master` 来 merge 上游分支的修改
  2. 直接运行`git submodule update --remote`, Git 将会自动进入子模块然后抓取并更新

更新后重新提交一遍, 子模块新的跟踪信息便也会记录到仓库中.
