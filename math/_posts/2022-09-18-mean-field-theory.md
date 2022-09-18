---
layout: post
title: "Mean Field Theory"
date: 2022-09-18 15:52 +0900
dir: /math/
tags: "統計"
description: "平均場近似"
---

## 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [Lions](#lions)
<!-- - [まとめ](#まとめ) -->
- [参考](#参考)

## Key word
- Mean Field Theory, 平均場近似
- Lions
- N点渦系，Gibbs測度

## はじめに
$ N $体問題を$ 1 $体問題に帰着する平均場近似ついて，整理します．
相互作用のある$ N $個の粒子を，近似的に「独立に」扱えることを仮定し平均的な$ 1 $粒子系に帰着するのが平均場近似です．
近似的な独立性の仮定は"Propagation of Chaos"と呼ばれ，重要です．

## Lions
Lionsらは，平面上正$ N $点渦系に対してカノニカルアンサンブルを適用し，平均場近似を数学的に取り扱いました．
$ N $点渦系の不変測度に対して，$ j $点同時分布$ \rho_j^N $を考えその弱収束極限$ \rho_j $がある測度$ \rho $の積測度でかけること

$ \rho_j^N \overset{w}{\rightarrow} \rho_j = \rho^{\otimes j} $

を以て，Propagation of Chaosを定式化しました．
さらに，極限密度の特徴づけとして，平均場方程式(MFE: Mean Field Equation)と自由エネルギー汎関数の最小化問題を導きました．

<!-- ## まとめ -->

## 参考
- Lions et al. *A special class of stationary flows for two-dimensional Euler equations: a statistical mechanics description*, Communications in Mathematical physics, 1992.