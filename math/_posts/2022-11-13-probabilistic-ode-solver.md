---
layout: post
title: "Probabilistic ODE Solver"
date: 2022-11-13 12:58 +0900
dir: /math/
tags: "UQ"
description: "Probabilistic ODE Solver"
---

## 目次
- [Key word](#key-word)
- [概要](#概要)
- [参考](#参考)

## Key word
- ODE
- Probabilistic Numerics

## 概要
Winner過程の積分を用いて確率的にODEを解く方法についてのメモ．

ODEの初期値問題 

$ y'(t) = f(t, y), \quad y(0) = y_0 $

を解くために，Winner過程を走らせて，ODEに合わせる作業する．

状態変数として，$ y'$に対応するWinner過程 $ W^1 $とその積分 $ W^0 $($ y $に対応)を考える．

$ W^0 = W^1 dt, \quad W^1_t = dB_t $

観測 $ H: \begin{bmatrix}
W^0 \\
W^1 
\end{bmatrix} \rightarrow \begin{bmatrix}
0 \\
f(t, y)
\end{bmatrix} $ により状態を補正．

補正にはKalman Filterを用いる．

### メリット
- implicitにODEを解ける．

## 参考
- [ODE Solver Research](https://www.probabilistic-numerics.org/research/ode/)
- [probabilistic-numerics.org](https://www.probabilistic-numerics.org/)
- [ProbNum Docs](https://probnum.readthedocs.io/en/latest/)
- [https://arxiv.org/pdf/2012.08202.pdf](https://arxiv.org/pdf/2012.08202.pdf)
- [https://arxiv.org/pdf/1610.05261.pdf](https://arxiv.org/pdf/1610.05261.pdf)