---
layout: post
title: "ランキング変動動画の作成 [Colaboratory]"
date: 2021-08-29 18:00 +0900
dir: /programming/
tags: ['Python', 'visualization']
description: "Bar Chart RaceというPythonのライブラリを使って時系列データからランキング変動動画を作成します．"
---
## Key word
- Python, Colab
- Bar Chart Race

## はじめに
Bar Chart RaceというPythonのライブラリを使って時系列ランキングデータからランキング変動動画を作成します．

環境はGoogle Colaboratoryを想定しています．

## Quick Start
ライブラリに付属したサンプルデータ(Covid19)から動画を作成します．

### install

```python
!pip install bar_chart_race
```

### Covid19
```python
import bar_chart_race as bcr
import pandas as pd

data_covid19 = bcr.load_dataset(name='covid19')
bcr.bar_chart_race(df = df_covid19)
```
これでnotebookにうめこみ動画が表示されます．

## 自作擬似データ
プログラミング言語シェアランキングの擬似データを生成してそれを元に動画を作成します．

### データ生成

```python
# 設定
years = np.arange(2000, 2021)
langs = ['Python', 'Ruby', 'Java', 'C', 'Julia', 'Go', 'Javascript', 'Matlab', 'C++', 'C#', 'Fortran', 'PHP', 'Kotlin', 'Swift']

# データ生成
# 細かい説明は省略します．
# (num_years, num_langs) の形のデータであればなんでもOKです．
num_years = len(years)
num_langs = len(langs)

lang_share = np.random.rand(num_years, num_langs)**2
lang_share += np.random.rand(num_langs)**2
lang_share = lang_share.cumsum(axis=0)

df_lang = pd.DataFrame(data=lang_share, index=years, columns=langs)
df_lang = (df_lang.T / df_lang.sum(axis = 1)).T
df_lang = (df_lang * 100).round(2)

print(f'shape: {df_lang.shape}')
df_lang.head()
```

### 動画作成
```python
# filenameをmp4で指定するとそこに保存してくれます．
filename = None # or 'path/to/dir/filename.mp4'

# 動画生成
# 注意：言語シェア率の表示fmtを指定できない．
bcr.bar_chart_race(df = df_lang, title = "Language Share Growth (Pseudo Data)", filename=filename, n_bars=10,
                   cmap='accent', bar_kwargs={'alpha': .2, 'ec': 'black'}, period_fmt='{x: .0f}', )
```

## サンプルコード
[ここに置いてあります．](https://github.com/KotaTakeda/bar_chart_race_demo/blob/main/demo.ipynb)

## まとめ
Pythonライブラリ`bar_chart_race`を使用してランキングの時間変動を動画として可視化しました．`pandas`さえ扱うことができれば簡単に作ることができます．オプションによる細かい表示の調整などが足りないこともあるので各自で実装の必要があります．

## 参考
- [dexplot/bar_chart_race, 2021-08-29](https://github.com/dexplo/bar_chart_race)
- [Bar Chart Race Official Document, 2021-08-29](https://www.dexplo.org/bar_chart_race)
