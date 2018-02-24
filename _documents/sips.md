---
layout: post
title: sips
date: 2018-02-21
tags: Library
---

scriptable image processing system (sips)  
"This tool is used to query or modify raster image files and ColorSync ICC profiles.  Its functionality can also be used through the "Image Events" AppleScript suite." とのこと．（公式ページより引用）  
MacOSX固有の画像処理コマンド

### flip
```bash
sips -f horizontal <path> # 水平フリップ
sips -f vertical <path> # 垂直フリップ
```