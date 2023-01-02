---
layout: post
title: "Mean Field Theory"
date: 2022-09-18 15:52 +0900
dir: /math/
tags: "統計"
description: "平均場近似"
---
## Key word
- Mean Field Theory, 平均場近似
- Lions
- N点渦系，Gibbs測度

## はじめに
$ N $体問題を$ 1 $体問題に帰着する平均場近似ついて，整理します．
相互作用のある$ N $個の粒子を，近似的に「独立に」扱えることを仮定し平均的な$ 1 $粒子系に帰着するのが平均場近似です．
近似的な独立性の仮定は"Propagation of Chaos"と呼ばれます．

## N点渦系｜Lionsらの方法
[関連PDF： Lions1992](pdf/lions1992.pdf)

### モデルの概要
$ N $点渦系は$ 2 $次元Euler方程式に従う流れの渦度場を $ N $ 個の均質な渦粒子で近似するモデルです．
平面内の領域 $ \Omega $ において循環 $ \Gamma > 0 $ の渦が $ N $点ある場合を考えると，
$ N $点の相互作用は$ 2 $点間相互作用 $ G(x, y) = -\frac{1}{2\pi} \log \|x - y\| $ の和で表され，ハミルトニアンと呼ばれます．

$ H = \frac{\Gamma^2}{2} \sum_{i=1}^N \sum_{i \neq j}^N G(x_i, x_j) $.

$ N $点渦系は $ H $ を保存するハミルトン系となるので，カノニカルアンサンブルを適用することで不変測度が以下で与えられます．

$ \varpi(x_1, \dots, x_N) = \frac{e^{-\beta H}}{\int e^{-\beta H} dx_1 \dots dx_N} $.

### 平均場近似
Lionsらは，平面上正$ N $点渦系に対してカノニカルアンサンブルを適用し(上の設定)，平均場近似を数学的に取り扱いました．
$ N $点渦系の不変測度に対して$ j $点同時分布 $ \rho_j^N $ を考え，その弱収束極限 $ \rho_j $ が存在する時にある測度 $ \rho $ の積測度でかけること

$ \rho_j^N \overset{w}{\rightarrow} \rho_j = \rho^{\otimes j} $

を以て，Propagation of Chaosを定式化しました．
さらに，極限密度の特徴づけとして，平均場方程式(MFE: Mean Field Equation)と自由エネルギー汎関数の最小化問題を導きました．

<!-- ## まとめ -->

## 参考
- Lions et al. *A special class of stationary flows for two-dimensional Euler equations: a statistical mechanics description*, Communications in Mathematical physics, 1992.