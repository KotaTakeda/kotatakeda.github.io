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
- [まとめ](#まとめ)
- [参考](#参考)

### Key word
- サンプリング, MCMC
- ハミルトニアンモンテカルロ

### はじめに
BetancourtのHamiltonian Monte Carlo(HMC)についてのsurvey論文を基にしています ．HMCの理論的背景を数学的な詳細には立ち入らず，物理的なイメージも交えて直感的に説明します．

### MCMC
まず，ランダムサンプリングの基本であるMalkov Chain MonteCalro(MCMC)について説明します．この方法は直感的であり実装も非常に単純ですが，計算効率が悪く得られる結果の有効性についての理論的保証も弱いです．
例えば最も簡単なRandom Walk MetropolisというMCMCアルゴリズムは以下のようになっています．

Random Walk Metropolis:
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
パラメータ空間に運動量を加えて位相空間に拡張します[^projection]．$ q \rightarrow (q,p) $

主に(1)Hamiltonianを保存するようにdeterministicに動き， その後 (2)stochastic に別の等Hamiltonian(エネルギー)面に移動するという2stepを繰り返す．

(1): Hamiltonianを保ったまま移動．$ (q,p) \rightarrow (q',p') $

(2): 別のエネルギー面に移動(運動量をstochasticに取り替え)．$ (q',p') \rightarrow (q',\tilde{p'}) $

```
q[0] = q_0
for n
  draw p from N(0, M)
  q', p' = hamilton_flow(q[n],p)
  q[n+1] = q' with probability min{1, exp(H(q,p) - H(q',p'))}
```

このような HMC
のサンプリングは効率がよく，得られる結果の有効性も理論的に広く保証されています．
積分時間やエネルギー遷移などHMCの実装上の自由度が残されておりそのチューニングや複雑化に改善の可能性があります．


### PDF
[詳細はこちら](/math/pdf/intro_to_hmc.pdf)

### まとめ
Hamiltonian Monte Carloのsurvey論文を読んで学んだことをまとめました． HMCは1980年代末期に登場した新しい技術なのでまだ研究の余地がありそうです．
今後は効率や結果の有効性について詳しく見ていこうと思います．

### 参考
-  Michael Betancourt. A conceptual introduction to hamiltonian monte carlo, 2018

### 注意
[^projection]:好きな時に射影してパラメータ$ q $を得ることができます．
