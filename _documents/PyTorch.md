---
layout: post
title: PyTorch
date: 2018-02-21
use_math: true
tags: Library
---

### `torch.Tensor.clamp_(min, max)` -> Tensor
`y = x.clamp_(min, max)`とするとx, yの値は以下の式に従う．

$$
\begin{eqnarray}
y_i
=
\begin{cases}
min & if \quad x_i \lt min \\
x_i & if \quad min \leq x_i \leq max \\
max & if \quad x_i \gt max
\end{cases}
\end{eqnarray}
$$

---

### class `torchvision.transforms.ToTensor`
`__call__(pic)` -> Tensor  
[0, 255]のPIL Imageかnumpy.ndarray (HxWxC)を[0.0, 1.0]のtorch.FloatTensor (CxHxW)に変換．  
レンジが変わることを知らずにはまった．

---

### class `torchvision.transforms.ToPILImage(mode=None)`
`__call__(pic)` -> PIL Image  
Tensor (CxHxW)かnumpy ndarray (HxWxC)をPIL Imageに変換する．  
ピクセルレンジは変わらない．  
...と書いてあるが，ソースコードを見ると`pic`が`torch.FloatTensor`だとピクセル値が255倍されるっぽい(↓)  
モデルの出力はだいたい`torch.FloatTensor`だから，入力で`transforms.ToTensor`を使わなかった場合は`transforms.ToPILImage`は使わないほうが良いかも．  
```python
if isinstance(pic, torch.FloatTensor):
        pic = pic.mul(255).byte()
```

### class `torch.nn.CrossEntropyLoss(weight=None, size_average=True, ignore_index=-100, reduce=True)`