---
layout: post
title: 便利なコマンド
date: 2019-07-01
tags: programming
---

### ファイルを複数のディレクトリにコピー
`hoge/`下の`piyo*`という全てのディレクトリに`src.txt`がコピーされる．
```bash
find hoge/ -name "piyo*" -type d -exec src.txt {} \;
```