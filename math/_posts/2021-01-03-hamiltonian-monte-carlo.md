---
layout: post
title: "Survey of Hamiltonian Monte Carlo"
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
- Hamiltonian Monte Carlo

### はじめに
Hamiltonian Monte Carloのsurvey論文を基にしています．

Betancourt の survey 論 文 [12] を 基 に し て い ま す ．本 稿 は Hamiltonian Monte
Calro)(HMC の理論的背景を数学的な詳細には立ち入らず，物理的なイメージも交え
て直感的に説明します．

### MCMC
まず，ランダムサンプリングの基本である Malkov Chain Monte
Calro(MCMC) について説明する．この方法は直感的であり実装も非常に単純だが，計算効
率が悪く得られる結果の有効性の保証も弱い．
例えば最も簡単なRandom Walk Metropolisのアルゴリズムは以下

Random Walk Metropolis:
```
q[0] = q_0
for n
  take q' from N(q[n], sigma)
  q[n+1] = q' with probability min(1, pi(q')/pi(q[n]))
```

### Hamiltonian Monte Carlo

#### 発想
HMC は生まれた当初は Hybrid Monte Carlo という呼び名ついていたように，gradient の
情報を利用した deterministic な遷移と stochastic な遷移を合わせてサンプリングを行う．勾配法のように目的の分布の勾配の情報を使えばいいのではないかと考えたのが始まりです．しかし，ただ勾配に従って点を動かすとmodeに落ちていくだけなので運動量を加えてうまく点をコントロールします．

#### アルゴリズム概略
パラメータ空間に運動量を加えて位相空間に拡張します[^projection]．$ q \rightarrow (q,p) $

(1)Hamiltonian を保存するように deterministic に動き，その後 (2)stochastic に別の等 Hamilton 面に移動するという 2step を繰り返す．

(1): Hamiltonianを保ったまま移動．$ (q,p) \rightarrow (q',p') $

(2): 別のエネルギー面に移動(運動量をstochasticに取り替え)．$ (q',p') \rightarrow (q',\tilde{p'}) $

このような HMC
のサンプリングは効率がよく，得られる結果の有効性も理論的に広く保証されています．
積分時間やエネルギー遷移など HMC 実装上の自由度が残されておりそのチューニングや複雑化に改善の可能性があります．


### PDF
[詳細はこちら](/math/pdf/intro_to_hmc.pdf)

### まとめ
Hamiltonian Monte Carloのsurvey論文を読んで学んだことをまとめました．HMCは1980年代末期に登場した新しい技術なのでまだ研究の必要がありそうです．
今後はMonte Carlo法の効率や結果の有効性の証明を詳しく見ていこうと思います．

### 参考
-  Michael Betancourt. A conceptual introduction to hamiltonian monte carlo, 2018

### 注意
[^projection]:好きな時に射影してパラメータ$ q $を得る．