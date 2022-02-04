---
layout: post
title: "Latex Tips"
date: 2021-02-11 17:34 +0900
dir: /programming/
tags: ["Latex", "メモ"]
description: "Latexに関するTipsをまとめています．"
---

### 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [まとめ](#まとめ)
- [参考](#参考)

### Key word
- Latex

### はじめに
LatexについてのTipsを備忘録として書いていきます．
随時更新します．

### まとめ
#### 定理の名前
```
\begin{thm}[定理の名前]
```

#### tilder
$ \sim $
```tex
\sim
```

上付き：$ \tilde{x} $
```tex
\tilde
```
上付き大きめ：$ \widetilde{P} $
```tex
\widetilde{}
```

#### 数列空間 $ \ell^2 $
小文字lの筆記体は以下のように書く．
```tex
\ell
```

#### 集合包含
$ A \subsetneq B $: 真部分集合
```tex
\subsetneq
```

#### 二項係数(組み合わせ)
$ \binom{n}{k} $: 縦ベクトルの表示
```tex
\binom{above}{below}
```

#### 斜体など
イタリック
```tex
\textit{イタリックにしたいアルファベット}
```

#### url
urlパッケージを使う．hyphensパラメータを渡すと折り返してくれる．
```tex
\usepackage[hyphens]{url}
```

#### 目次
```tex
\tableofcontents
```

#### 3点ドット
横：$ x_1, \dots, x_N $ or $ x_1 + \dots + x_N $
```tex
\dots
```
縦：\vdots
```
\vdots
```
斜め：$ \ddots $
```tex
\ddots
```

#### ラプラシアン
$ \triangle $
```tex
\triangle
```

### 参考
- [tex wiki, 2021-02-11](https://texwiki.texjp.org/)

### 更新
- 2022-02-05
