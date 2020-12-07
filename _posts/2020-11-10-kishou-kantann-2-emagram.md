---
layout: post
title: "エマグラムに関する知識"
date: 2020-11-10 17:34 +0900 
tags: '気象予報士'
---

### 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [解析](#解析)
- [大気の安定性](#大気の安定性)
- [まとめ](#まとめ)
- [参考](#参考)

### Key word
- エマグラム，高層気象観測
- SSI, CAPE, CIN

### はじめに

気象予測の現場ではエマグラムは過去のデータのためあまり利用されません．
大気の状態を解析する題材として気象予報士試験ではよく出題されます．

### エマグラムの定義と見方

#### 定義
エマグラムとは

- 横軸に気温，縦軸に気圧を対数目盛でとり，
- ある地点の上空で観測された気圧-気温，気圧-露点温度の関係(状態曲線)をプロットした図です．
- さらに，補助線として乾燥断熱線，湿潤断熱線，等飽和混合比線がそれぞれ複数引かれています．
- 気圧の減少が高度の上昇に対応します．

補助線について

|補助線|説明|
|---|---|
|乾燥断熱線| 未飽和の空気を断熱的に上昇・下降させたときの気圧-気温の関係を表す直線です．|
|湿潤断熱線| 飽和した空気を断熱的に上昇・下降させたときの気圧-気温の関係を表す直線です．|
|等飽和混合比線| 飽和混合比(g/kg)[^mixing_ratio]が一定となる気圧-気温の関係を表す曲線です．露点温度は直線に沿って変化します．|

#### コメント
- 露点温度の状態曲線は必ず気温の状態曲線の左に現れます．

### 大気の安定性
#### 擬似断熱上昇曲線
*下層*の空気を上昇させた時の温度変化です．この書き方についてまとめます．
1. 地上の露点，気温を見つける
2. 地上の気温を通る乾燥断熱線に沿って空気を上昇させる．
3. 地上の露点をを通る等飽和混合比線と2の交点からは空気が飽和しているので湿潤断熱線に沿って空気を上昇させる．

特別な高度
- 3.での交点を持ち上げ凝結高度という．
- 3.以降で擬似断熱上昇曲線と実際の大気の温度の状態曲線との交点を自由対流高度という．

#### 安定性に関する指標
1. SSI(showalter stability index, ショワルターの安定指数): 
  - 定義: (実際に観測された500hPaの温度) - (850hPaの空気を500hPaまで擬似断熱上昇させた温度)
  - SSIが負の値となるとき850hPaの空気が500hPaまで上昇したとき周りの空気より温度が高くなり浮力を得てさらに上昇します．(つまり不安定)
  - 逆にSSIが正の値のとき大気は安定と判断できます．
  - SSIが-7以下になると極めて不安定と言えます．
2. CAPE(convective avalable potential energy, 対流有効位置エネルギー):
  - 空気が自由対流高度より上昇したときに浮力による空気の上昇の強さを表します．
  - 自由対流高度と平衡高度と間で擬似断熱上昇曲線と実際の大気の状態曲線に囲まれる面積に対応します．
  - 詳細な定義は割愛します．
3. CIN(convective inhibition, 対流抑制):
  - 地上の空気を自由対流高度まで持ち上げるために必要なエネルギーの大きさです．
  - 詳細な定義な割愛します．



### まとめ
- 高層気象解析に使われるエマグラムに関する知識をまとめました．
- 空気塊の断熱上昇時の温度と湿度それに空気塊に対する浮力がpointでした．
- 大気の安定性の指標も複数紹介しましたがそれらを合わせて総合的に安定性を判断する必要があります．

### 参考
- らくらく突破気象予報士簡単合格テキスト 学科専門知識編 Chapter2
- [エマグラム wikipedia](https://ja.wikipedia.org/wiki/%E3%82%A8%E3%83%9E%E3%82%B0%E3%83%A9%E3%83%A0) - 2020/11/10

### 注意
[^mixing_ratio]: 乾燥空気1kgに対する飽和水蒸気量(g)