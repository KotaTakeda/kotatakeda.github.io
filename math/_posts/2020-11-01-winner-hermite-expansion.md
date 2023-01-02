---
layout: post
title: "Winner Hermite Expansion"
description: "確率場やrandom ODEの解を表現する方法のひとつであるWinner Hermite展開"
date: 2020-11-01 21:00 +0900
dir: /math/
tags: ['スペクトル理論', 'UQ']
---
## Key word
- Hermite多項式，gPC
- random ODE

## はじめに
物理や数学の様々な場面で登場するHermite多項式ですが今回はその直交性に注目し，
Hermite多項式による$L^2$関数の直交展開についてまとめます．

正規分布に従うランダム性を直交展開の係数により表現することができます．

## Hermite多項式
### 定義
$ H_n(x) = (-1)^n e^{-x^2} \frac{d}{dx} e^{-x^2} $

を満たす多項式をHermite多項式という．

定数倍の自由度があるがここでは最高次数を1とする．

### 性質
1. $ (H_n)_{n \in \mathbb{N}_0} $は$ L^2(\mathbb{R}, \gamma;\mathbb{R}) $の直交基底となる．(ただし，$ \gamma = N(0,1) $)
2. $ \frac{d}{dx} H_n(x) = n H_{n-1}(x) $
3. $ H_n(x+h) = \sum_{k=0}^n {}_n C_k h^{n-k} He_k(x) $
4. その他，多数の特筆すべき性質を持つがここでは省略．

## Winner-Hermite polynomial chaos expansion
ここがメインです．
Hermite多項式で$ L^2 $関数を展開します．

詳細は[pdfリンク](/math/pdf/chapter11.pdf)のHermite多項式の箇所．

## まとめ
- 直交多項式による$ L^2 $関数の展開の中でも基本的なHermite多項式による展開をまとめました．
- random ODEに応用することができます．

## 参考
- Timothy John Sullivan. *Introduction to uncertainty quantification*, Springer, 2015.

## 注意
### Notation
- $ \mathbb{N}_0 = \mathbb{N} \cup \{ 0 \} $
- 平均$ m $, 標準偏差 $ \sigma $の正規分布を$ N(m, \sigma^2) $とかく．
