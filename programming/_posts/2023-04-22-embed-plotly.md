---
layout: post
title: "Plotly埋め込み"
date: 2023-04-22 13:00 +0900
dir: /programming/
tags: "Python"
description: "PlotlyをHTMLで出力しwebサイトに埋め込みます．"
---


## Key word
- Plotly

## はじめに
PlotlyをHTMLで出力しwebサイトに埋め込みます．


<iframe src="../code/torus_demo.html" width="80%" height="400px"></iframe>

## コード
出力
```python
import plotly.graph_objects as go

data = # 何らかのplotをする
fig = go.Figure(data)
fig.write_html("plotly.html", include_plotlyjs='cdn',full_html=False)
```

埋め込み
```html
<iframe src="path/to/plotly.html" width="80%" height="400px"></iframe>
```
<!-- ## 参考 -->