title: selenium with python自动化实践笔记
date: 2016-11-22 20:53:18
tags:
- selenium
- python
- PhantomJS
---
# 前言
之前一直用Requests、BeautifulSoup实现一些小脚本，老是要抓包而且由于异步加载的问题有很多js的坑，所以打算试试PhantomJS
练手的脚本是联通的[一起沃](http://17wo.cn/)自动签到

# 实践中遇到的一些坑
## phantomJS无法在crontab下被调用
### 分析原因
环境变量问题，经测试crontab下的`PATH=/usr/bin:/bin`,而phantomjs安装在`/usr/local/bin`
### 解决方案
1.在shell脚本中加入`source /etc/profile`,比如这样
```shell
#!/bin/bash
echo $PATH
source /etc/profile
cd /home/pi/Scripts/17wo/
python3 17wo_s.py
echo $PATH
```
2.追加phantomjs所在的文件路径到`PATH`
```shell
your shell cmd...
export PATH=$PATH:/usr/local/bin
...
```
.
├── 17wo_s.py
├── captcha.jpg
├── cookies
├── cron.log
├── damatuWeb.py
├── ghostdriver.log
├── logger.log
└── start.sh