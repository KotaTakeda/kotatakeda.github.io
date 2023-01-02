---
layout: post
title: "Vega-Liteの埋め込み"
date: 2022-04-24 15:30 +0900
dir: /programming/
tags: "visualization"
description: "データ可視化用フォーマットであるVega-Liteによるグラフィックをwebページに埋め込むためのメモ．"
---
## Key word
- データ可視化
- Vega-Lite

## はじめに
データ可視化用フォーマットである[Vega-Lite](https://vega.github.io/vega-lite/)によるグラフィックをwebページに埋め込み方をまとめます．埋め込み用データの準備は別で行う必要があり，その説明は省きます．

## 埋め込み
[サンプルページ](/programming/code/vega_lite_sample.html)

### 必要なこと・もの
- vega-liteフォーマットのjson（可視化用データから作ります．）
- vega-lite用のjsスクリプト読み込み
- htmlへの埋め込みコード

### HTMLの基本形
```html
<!DOCTYPE html>
<html>
<head>
  <script type="text/javascript" src="https://cdn.jsdelivr.net/npm//vega@5"></script>
  <script type="text/javascript" src="https://cdn.jsdelivr.net/npm//vega-lite@4.17.0"></script>
  <script type="text/javascript" src="https://cdn.jsdelivr.net/npm//vega-embed@6"></script>
</head>
<body>
  <div id="vis"></div>
  <script>
    (function(vegaEmbed) {
      var spec = {}; // Vegaフォーマットの可視化用データ(json)が入る．
      var embedOpt = {"mode": "vega-lite"};
      const el = document.getElementById('vis');
      vegaEmbed("#vis", spec, embedOpt)
        .catch(console.warn);
    })(vegaEmbed);

  </script>
</body>
</html>
```
Pythonライブラリの[Altair](https://altair-viz.github.io/)を使うとPandasデータフレームからグラフィックの作成，htmlのエクスポートまで行うことができます．

## 参考
- [Vega-Lite – A Grammar of Interactive Graphics](https://vega.github.io/vega-lite/)
