---
layout: post
title: "Latex Tips"
date: 2021-02-11 17:34 +0900
dir: /programming/
tags: "Latex"
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
```
\sim 
%=> ~

\tilde
%=> 上付き ~
```

#### 数列空間 $ \ell^2 $
小文字lの筆記体は以下のように書く．
```
\ell
```

#### 集合包含
$ A \subsetneq B $: 真部分集合
```
\subsetneq
```

#### 二項係数(組み合わせ)
$ \binom{n}{k} $: 縦ベクトルの表示
```
\binom{above}{below}
```

#### 斜体など
イタリック
```
\textit{イタリックにしたいアルファベット}
```

#### url
urlパッケージを使う．hyphensパラメータを渡すと折り返してくれる．
```
\usepackage[hyphens]{url}
```

#### 目次
```
\tableofcontents
```

#### 3点ドット
横(下): $ A \dots $
```
\dots
```

横(真ん中): $ A \cdots $
```
\cdots
```

縦: $ \vdots $
```
\vdots
```

斜め: $ \ddots $
```
\ddots
```

<!-- ### 参考
### 注意 -->