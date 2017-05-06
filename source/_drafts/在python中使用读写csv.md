---
title: 在python中使用读写csv
date: 2016-05-28 22:04:12
tags:
---
保存的csv文件excel读取为乱码
解决方案,在写前加入UTF8的BOM
```python
import codecs
······
filename = 'btsynckeys.csv'
with open(filename,'wb') as f:
    f.write(codecs.BOM_UTF8)
csvfile = open(filename, 'a')
```