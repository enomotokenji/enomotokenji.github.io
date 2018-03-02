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
### リスト内に指定の値を持つ要素が存在するかどうか
```python
<value> in <list>
# example
list = ['a', 'b', 'c']
'a' in list #-> True
'd' in list #-> False
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
---
### 辞書型のキー取得
```python
<dict>.keys() #-> list
```