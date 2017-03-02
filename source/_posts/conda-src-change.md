---
title: 修改conda为国内源
date: 2016-07-16 10:30:01
tags:
- Anaconda
- conda
- python
- 源
---
Anaconda 是一个用于科学计算的 Python 发行版，支持 Linux, Mac, Windows, 包含了众多流行的科学计算、数据分析的 Python 包。
Anaconda 安装包可以到 https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/ 下载。
TUNA 还提供了 Anaconda 仓库的镜像，运行以下命令:
```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```
即可添加 Anaconda Python 免费仓库
经测试，[清华镜像源](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)的帮助说明中多了引号，取消后正常
运行 `conda install numpy` 测试一下吧。