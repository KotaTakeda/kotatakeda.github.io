---
layout: post
title: "Survey of Hamiltonian Monte Carlo"
description: "近年注目されているサンプリング法，ハミルトニアンモンテカルロの紹介"
date: 2021-01-03 12:27:00  +0900
dir: /math/
tags: 'サンプリング'
---

### 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [MCMC](#mcmc)
- [Hamiltonian Monte Carlo](#hamiltonian-monte-carlo)
- [詳細](#詳細)
- [まとめ](#まとめ)
- [参考](#参考)

### Key word
- サンプリング, MCMC, ハミルトニアンモンテカルロ(Hamiltonian Monte Carlo: HMC)
- ハミルトン力学
- ベイズ推定，数値積分

### はじめに
Betancourtのハミルトニアンモンテカルロ(Hamiltonian Monte Carlo: HMC)についての論文を基にしています ．HMCの理論的背景を数学的な詳細には立ち入らず，物理的なイメージも交えて直感的に説明します．HMCはベイズ推定における事後分布の推定や統計量の数値的な計算時に使用するのが主な目的です．

[詳細な資料までjump↓](#詳細)

### MCMC
まず，ランダムサンプリングの基本であるMalkov Chain MonteCalro(MCMC)について説明します．この方法は直感的であり実装も非常に単純ですが，計算効率が悪く得られる結果の有効性についての理論的保証も弱いです．
例えば最も簡単なRandom Walk MetropolisというMCMCアルゴリズムは以下のようになっています．

```
q[0] = q_0
for n
  draw q' from N(q[n], sigma)
  q[n+1] = q' with probability min(1, pi(q')/pi(q[n]))
```
Random Walkという名前の通り各stepで現在の点の近くからランダムに次の点の候補を取り，現在の点と確率密度の値を比べて候補の値が大きいほど採用されやすいようになっています．

### Hamiltonian Monte Carlo

#### 発想
HMC は生まれた当初は Hybrid Monte Carlo という呼び名ついていたように， gradientの
情報を利用したdeterministicな遷移とstochasticな遷移を合わせてサンプリングを行います． 勾配法のように目的の分布の勾配の情報を使えばいいのではないかと考えたのが始まりです．しかし，ただ勾配に従って点を動かすと極に落ちていくだけなので運動量を加えてうまく点をコントロールします．

#### アルゴリズム概略
サンプルの過程でパラメータ空間に運動量$ p $を加えて位相空間に拡張します[^projection]．$ q \rightarrow (q,p) $

以下のようにして$ q_{old} $から$ q_{new} $を作ります．

(1): 運動量のサンプル．$ q_{old} \rightarrow (q_{old}, p) $

(2): Hamilton flowに沿って移動．$ (q_{old}, p) \overset{hamilton flow}{\rightarrow} (q_{new}, p_{new}) $

```
q[0] = q_0
for n
  draw p from N(0, M)
  q', p' = hamilton_flow(q[n],p)
  q[n+1] = q' with probability min{1, exp(H(q,p) - H(q',-p'))}
```

このような HMC
のサンプリングは効率がよく，得られる結果の有効性も理論的に広く保証されています．
積分時間やエネルギー遷移などHMCの実装上の自由度が残されておりそのチューニングや複雑化に改善の可能性があります．


### 詳細
HMCについて詳しくまとめたpdfがあります．[^update]
- [HMCのIntroduction](/math/pdf/intro_to_hmc.pdf)
- [HMCのMap](/math/pdf/map_of_hmc.pdf)
- [HMCのスライド](/math/pdf/intro_to_hmc_slide.pdf)

### まとめ
HMCの紹介論文を読んで学んだことをまとめました． 
統計学における必要性から幅広い応用が期待されると共に理論的な研究も奥が深そうです，

### 参考
-  Michael Betancourt. A conceptual introduction to hamiltonian monte carlo, 2018

### 注意
[^projection]:好きな時に射影してパラメータ$ q $を得ることができます．
[^update]:更新する場合があります．
