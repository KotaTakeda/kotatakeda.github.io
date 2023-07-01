---
layout: post
title: "データ同化における数値計算テクニック"
date: 2023-07-01 15:40 +0900
dir: /math/
tags: "データ同化"
description: "データ同化における数値計算上のテクニックと数学的な説明について整理する．"
---

## 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [テクニック](#テクニック)
<!-- - [参考](#参考) -->

## Key word
- データ同化
- inflation, localization

## はじめに
データ同化では，数値計算上でad hocに行われてきたテクニックがいくつかある．
数学的な理解がまだ少ないものについて整理する．

## テクニック
### Covariance inflation
Ensemble Kalman Filterにおいて，予測誤差共分散行列(Covariance) $ P^f $の縮退を防ぐ方法．
数学的には$ P^f $の固有値を大きくする操作と言える．
$ h > 0 $に対して，additive inflation $ P^f \rightarrow P^f + \alpha I $は固有値の下限が保証されるので扱いやすい．
一方で，multiplicative inflation $ P^f \rightarrow (h+1) P^f $は固有値の下限が$ 0 $になりうるので扱いが難しい．

### Localization
物理モデルの遠方相互作用が小さいことを仮定して，計算から遠方の効果を除く方法．
対角付近以外の成分が0となるlocalization matrix $ \phi $が用いられる．
$ \phi_{i,j} = \rho(d(i,j)/l) $という各成分の距離に基づく形をしている．
近年は物理モデルの定式化とlocalization時の評価についての研究が出てきている．

#### Covariance localization
グリッド間の誤差相関を表す予測誤差共分散行列 $ P^f $について $\phi $と成分ごとの積をとることで，対角行列に近い$ P^f \circ \phi $が得られ，$ P^f $のrankが改善される．

#### Observation localization
同化する変数の位置から遠い観測値を同化に用いない方法．
数学的な定式化をまだ見たことがない．
<!-- 各位置$ j $で$ \phi_i R^{-1} $とすることで実装できる． -->

<!-- ## 参考 -->