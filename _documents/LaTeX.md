---
layout: post
title: LaTeX
date: 2018-02-21
tags: Library
---


### 図
```
\begin{figure}[htbp]
  \begin{minipage}{0.5\hsize}
    \begin{center}
      \includegraphics[width=60mm, bb=0 0 w h]{figpath}
    \end{center}
    \subcaption{subcap}
    \label{fig: 1}
  \end{minipage}
  \begin{minipage}{0.5\hsize}
    \begin{center}
      \includegraphics[width=60mm, bb=0 0 w h]{figpath}
    \end{center}
    \subcaption{subcap}
    \label{fig: 1}
  \end{minipage}
  \caption{cap}
  \label{fig: example}
\end{figure}
```
---
### subcaption package
1行目: 設定を明記しておかないとsubcaptionに上書きされる(?)
2行目: 引用時図番号が括弧つきで表示されるオプション
3行目: captionとsubcaptionを両方使う時のエラー回避
```
\usepackage[hang,small,bf]{caption}
\usepackage[subrefformat=parens]{subcaption}
\captionsetup{compatibility=false}
```
---
### 数式内改行
`&`で位置合わせ
```
\begin{equation}
\begin{split}
a&=b+c
dd&=ee+ff
\end{split}
\end{equation}
```
---
### スペース
```
\quad #1文字スペース
\qquad #2文字スペース
```