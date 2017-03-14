---
title: conda使用笔记
date: 2017-03-13 22:26:54
tags:
---
#更新包
`conda update scipy`更新scipy
`conda update --all`更新所有包
## `conda update`相关参数解释
`-c CHANNEL, --channel CHANNEL`

#更换国内源
Anaconda 安装包可以到 https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/ 下载。
TUNA 还提供了 Anaconda 仓库的镜像，运行以下命令:
```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```
即可添加 Anaconda Python 免费仓库
运行 `conda install numpy` 测试一下吧。
