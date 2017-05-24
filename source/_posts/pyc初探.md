---
title: pyc初探
date: 2017-05-24 21:41:34
tags: python
---
#  什么是pyc文件和pyo文件
pyc文件是Python的字节码(byte code)文件，是一种二进制文件。pyc文件跨平台，由python的虚拟机加载执行。pyc文件与Python的版本有关，不同版本的Python编译出的pyc文件不同。

pyo文件是优化(optimize)后的字节码文件。

#  编译成pyc文件
python -m py_compile foo.py

#  编译成pyo文件

```python
# python3.5环境下测试无论带不带`-O`参数,都会只生成pyc文件
python -O -m py_compile foo.py
```