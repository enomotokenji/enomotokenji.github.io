---
layout: post
title: Photometric Stereo under Non-uniform Light Intensities and Exposures
date: 2018-04-05
use_math: true
tags: Paper
---

# どんなもの？
Photometric stereoの枠組みの中で各画像における入射光強度が一様でない場合のアプローチを提案．

# 先行研究と比べて何がすごい？
* 入射光強度が固定ではない
* 入射光の方向と強度以外の仮定がない

# 技術や手法の肝は？
## Alternating minimization method
albedo-scaled surface normal $B$とnon-uniform scalings $E$（入射光強度行列）それぞれに関する最小化問題を交互に最適化することで二つの未知行列を同時に求める．  
$B$に関する最適化によって誤差が小さくなったら，次の$E$に関する最適化も必ず誤差を小さくする．

# どうやって有効だと検証した？
合成データと実世界データそれぞれに対して，入射光強度もしくは露光時間が一様ではないセッティングで実験を行っている．  
比較手法は，Frobenius-norm minimization, robust L1-norm minimization, constrained bivariate regression (CBR).  
合成データ，実世界データともに提案手法が最も優れた結果であった．  
また，SQNRが高いデータに対してもロバストであることを示した．  
ただし，露光時間を一定にした実験では提案手法よりも既存手法が優れていた．（Table. 1）

# 議論はある？


# 次に読むべき論文は？

