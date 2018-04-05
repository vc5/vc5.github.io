---
title: Openwrt编译入门笔记
date: 2018-03-30 11:01:43
tags:
- Openwrt
- 编译
---
本文以斐讯K2为例，进行编译
# 使用编译包
## [部署编译环境][1]
[1]:https://openwrt.org/docs/guide-developer/quickstart-build-images "Quick Image Building Guide"

### 注意事项

1.不要用root用户编译

### Docker下简易部署

`docker run -t -i nemoalex/openwrt-buildroot /bin/bash`
### 在Ubuntu系统下自行部署
安装以下依赖就好了
```bash
sudo apt-get install subversion g++ zlib1g-dev build-essential git python rsync man-db
sudo apt-get install libncurses5-dev gawk gettext unzip file libssl-dev wget zip
```


## 下载最新编译包
```bash
wget https://downloads.openwrt.org/snapshots/targets/ramips/mt7620/openwrt-imagebuilder-ramips-mt7620.Linux-x86_64.tar.xz
#从软件源更新所有软件包
tar xvfJ openwrt-imagebuilder-ramips-mt7620.Linux-x86_64.tar.xz
cd openwrt-imagebuilder-ramips-mt7620.Linux-x86_64
```

## 开始编译

`make image PROFILE=psg1218a PACKAGES="luci luci-i18n-base-zh-cn python-codecs python-logging python-openssl python-light -ip6tables -kmod-ip6tables" FILES=files`

其中`PROFILE`参数，可以用`make info`命令获取,本例中为`psg1218a`

`FILES`参数为存放配置文件的文件夹

其中`python-codecs python-logging python-openssl python-light`是为了运行python版drcom客户端准备的按需取用

# 从源码编译
## 同步源代码
```
git clone https://git.lede-project.org/source.git lede
cd lede

./scripts/feeds update -a
./scripts/feeds install -a

```
## 编译设置
使用`make menuconfig`来选择编译平台，选择你需要的软件（luci中文包，Python...）

## 编译
`make -j1 V=s`

`j1`代表使用单核编译,`V=s`(或者`V=99`)代表输出更详细的日志



# 编译失败可能的原因

1.内存不足，可以通过添加swap来解决

# Reference

[1.Quick Image Building Guide][1]
