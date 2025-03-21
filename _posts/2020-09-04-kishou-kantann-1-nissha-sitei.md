---
layout: post
title:  "日射と視程"
date:   2020-09-04 8:52:00 +0900
tag: '気象予報士'
description: '日射と視程についてまとめます．'
---
## Key word
- 日射，日照
- 視程

## はじめに
植物の生育にとって大事な日射・日照，航空機・船舶関連の運行で重要な視程についてまとめます．

## 日照・日射
### 分類
- 直達日射: 太陽光線から直接受ける光．
- 散乱光: 太陽光が空気分子で散乱した光．
- 全天日射: 直達日射 + 散乱光

### 観測
直達日射と全天日射を観測する．
1. 直達日射量: 基準値[^threshold]以上の直辰日射の積算時間を記録．アメダスでは6min単位で観測．太陽方向を常に向くように自動で動く筒状のセンサーで観測．
2. 全天日射量: 1日（日の出20分前から日没後20分まで）の積算時間のみ観測．水平面に設置された半球面で受けた単位面積あたりの放射強度を観測．

### 日照率

- 可照時間: 太陽の中心が東の地平線(または水平線)に現れてから西の地平線(または水平線)に沈むまでの時間の長さ.

- 日照率: 直達日射積算時間/可照時間


### 混濁係数
- 混濁係数: 大気中に浮遊している微粒子の量を測る指標．これが大きいと大気中に微粒子が多い．

- 日傘効果: 混濁係数が大きいと直達日射量が減少し(さらに散乱光は増加)，全天日射量も減少するので地上の平均気温が下がる．この現象を*日傘効果*という．

## 視程
- 視程: 360度見渡して最も見通しが悪い方位における視程距離を指す．航空関連では180度以上の代表的な視程の平均をとる．

### 天気と視程
- 霧ともや: 大気中に微小な水滴が浮遊している状態(湿度はほぼ100%)で視程によって現象の呼ぼかたが変わる．
  - もや: 視程が1km以上10km未満
  - 霧: 視程1km未満
  - 濃霧: 視程が陸上で100m以下, 海上で500m以下

### 煙霧・風塵・砂塵嵐
大気現象，天気(15種)のどちらとして扱うかによって定義が変わる．

- 大気現象
  - 煙霧: 乾いた微粒子(黄砂も含む)により視程が1km未満．
  - 風塵: 強風によって地表面上のちり・ほこりなどが舞い上がり一時的に視程が悪くなる現象．
  - 砂塵あらし: ちり・ほこり・砂などが空高く舞い上げられる．
- 天気(15種)
  - 煙霧: 大気現象としての煙霧が発生しているまたは煙霧において視程は1km以上であるが煙霧が原因で雲量が10と観測される場合．なお，煙霧と霧がある場合霧を優先
  - 大気現象の砂塵あらしがあって視程が1km未満のとき．

### スモッグ
- スモッグ: 大気汚染による煙霧をスモッグということがある．
- 光化学スモッグ: 炭化水素や窒素化合物が太陽の紫外線によって人体に有害なオキシダント生成され，大気中に浮遊する現象．
- PM2.5: 大気中に浮遊している大きさが2.5$\mu$m以下の微粒子．主に燃料の燃焼によって生じる．

## 参考
らくらく突破気象予報士簡単合格テキスト 学科専門知識編 Chapter1 6,7


## 注意
[^threshold]: 放射強度が$120W/m^2$以上．
