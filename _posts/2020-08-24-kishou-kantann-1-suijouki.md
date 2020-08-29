---
layout: post
title:  "水蒸気量の観測"
date:   2020-08-24 21:50:00 +0900
tag: '気象予報士'
---
### 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [大気中の水蒸気量の観測](#大気中の水蒸気量の観測)
- [相当温位と混合比](#相当温位と混合比)
- [乾燥空気と湿潤空気の成因](#乾燥空気と湿潤空気の成因)
- [前線](#前線)
- [参考](#参考)

### Key word
- 水蒸気圧，相対湿度，露点温度

### はじめに
大気の水蒸気量は呼吸器疾患，作物の生育，降水量の予報などに影響を与える．

### 大気中の水蒸気量の観測
#### 相対湿度
水蒸気量/飽和水蒸気量 を%で表したもの．
  - 観測は電気式温度計で行っている．[^humidity]
  - 乾湿計を用いる方法もある．乾球温度計と湿球温度計の温度差と気温から湿度を求める．

#### 露点温度
気温を下降させる過程で水蒸気圧と飽和水蒸気圧がはじめて等しくなる温度．
  - 観測は塩化リチウム露店計．塩化リチウムの吸湿性を利用している．


### 相当温位と混合比
試験で使われる近似式 [^derivative]

#### 相当温位
相当温位$ \theta_e $(K)を求める近似式:

$$
  \theta_e = \theta + kw
$$

ただし，$ \theta :$ 温位(K)，$ w: $ 湿潤空気塊の混合比(g/kg)，$ k :$ 比例定数(2.5~3.5が使用される．)

#### 混合比
混合比$ w $(kg/kg)を求める近似式:

$$
  w = 0.622 \frac{e}{P}
$$
ただし，$ e :$ 水蒸気圧(hPa)，$ P :$ 気圧(hPa)

### 乾燥空気と湿潤空気の成因
- 乾燥空気: 大気の下降による．
- 湿潤空気: 水滴の多量蒸発，上昇による断熱冷却による．

### 前線
#### 定義
前線とは「地上で水平温度傾度が大きくなっている等温集中帯の暖気川に沿った線」と定義されている．基本的には地上の前線を指す．

#### 梅雨前線
梅雨前線: 
- 等温線が集中せずに水平温度傾度が小さくなっていることがある．
- 代わりに北側200kmにわたって水蒸気密度傾度が大きくなる．

#### 天気図解析
- 寒冷前線，梅雨前線ともに等相当温位線が前線の寒気側に集中している．

### 参考
らくらく突破気象予報士簡単合格テキスト 学科専門知識編 Chapter1


### 注意
[^humidity]: 多数の気孔を持つセラミックや高分子化合物は周囲の湿度に応じて電気抵抗が変わる．この性質を利用する．
[^derivative]: 導出などは専門書を参照．