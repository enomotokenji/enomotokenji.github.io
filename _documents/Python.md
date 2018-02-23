---
layout: post
title: Python
date: 2018-02-22
use_math: true
tags: Library
---

### リストの最大値のインデックス
下記が一番速そう．  
最大値が複数あったら，一番若いindexが返ってくる．  
```python
<list>.index(max(<list>))
```
---
### 辞書型のソート
```python
# key sort
sorted(<dic>.items(), key=lambda x: x[0])
# value sort
sorted(<dic>.items(), key=lambda x: x[1])
# 辞書が入れ子になっている場合の子辞書のvalueソート
sorted(<dic>.items(), key=lambda x: x[1][<sub_key>])
```