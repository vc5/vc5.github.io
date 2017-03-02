---
title: 利用Python进行迭代计算
date: 2016-05-07 23:36:50
tags: 
- python
- csv
- math
- 迭代
---
<!-- more -->
源码如下
```python
import math
import csv

g = 9.8

def getk(k, t, d, j):
    k0 = k
    k1 = 4 * math.pow(math.pi, 2) / (math.pow(t, 2) * g * math.tanh(k * d))
    while abs(k1 - k0) > j:
        yield k0
        k0 = k1
        k1 = 4 * math.pow(math.pi, 2) / \
            (math.pow(t, 2) * g * math.tanh(k0 * d))

def get(k, t, d, j):
    pool = []
    res = getk(k, t, d, j)
    for i in res:
        pool.append(i)
    print("当T=%s,d=%s时，共计算%s次，最终结果为%s"
          % (t, d, len(pool) - 1, pool[-1]))
    return pool

with open("source.csv") as csvfile:
    reader = csv.DictReader(csvfile)
    out = open('out.csv', 'w')
    fieldnames_out = ['T', 'd', '迭代次数', '迭代结果']
    writer = csv.DictWriter(out, fieldnames=fieldnames_out)
    writer.writeheader()
    for row in reader:
        res = get(2, float(row['t']), float(row['d']), 0.001)
        writer.writerow(
            {'T': row['t'], 'd': row['d'],
             '迭代次数': len(res) - 1, '迭代结果': res[-1]})
    out.close()
```