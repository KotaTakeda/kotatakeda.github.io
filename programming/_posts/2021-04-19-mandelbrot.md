---
layout: post
title: "マンデルブロ集合の作図"
date: 2021-04-19 11:16 +0900
dir: /programming/
tags: ['教育', 'Python']
description: "マンデルブロ集合の作図を通してプログラミングを学びます．"
---
## Key word
- フラクタル，マンデルブロ集合
- 複素数平面
- Google Colaboratory, Python

## はじめに
フラクタル図形の中でも有名な[マンデルブロ集合](https://ja.wikipedia.org/wiki/%E3%83%9E%E3%83%B3%E3%83%87%E3%83%AB%E3%83%96%E3%83%AD%E9%9B%86%E5%90%88)の定義と作図を行います．
Google Colaboratoryを使って計算し，綺麗な図を描きます．

## 準備
### 前提知識
- 数学
  - 複素数平面
- プログラミング
  - Python: 代入，forループ，真偽値，関数，import
  - Google Colaboratory(Colab)が使える．

### マンデルブロ集合の定義
複素数$ c $に対して，

$ z_{n+1} = z_n^2 + c, z_0 = 0 $の漸化式で生成される複素数列$ (z_n)_n $が$ n \rightarrow \infty $の時に$ z_n < \infty $となるような複素数$ c $全体をマンデルブロ集合という．

### 環境
[Google Colaboratory](https://colab.research.google.com/)でPython3のnotebookを作成．
[参考, 2021-08-17](https://qiita.com/yamaza-h/items/503d175e8da349cbcb6c)

## コード
[Colabサンプルコード](https://colab.research.google.com/drive/171uAc1rtuadwrrlOy50ji173biQPWafE?usp=sharing)

### 準備
必要なライブラリをインポート
```python
%matplotlib notebook
import numpy as np
import matplotlib.pyplot as plt
import itertools

# アニメーション用
from matplotlib import animation, rc
from matplotlib.animation import PillowWriter
from IPython.display import HTML
```

### 判定する関数
複素数$ c $がマンデルブロ集合に属するか判定する関数．\\
input: `c`（複素数），output: マンデルブロ集合に属するかどうか（真偽値）
```python
def judge_mandelbrot(c, N):
  z = 0
  for _ in range(N):
      z = z*z + c
  return np.abs(z) < 1 # N回後に絶対値が1より小さいときは発散しないと判定
```
例えば，次のように使います．
```python
c = 0.2 + 0.1j
N = 50
judge_mandelbrot(c, N)
# => True
```

>補足
>- `N`が小さいと判定の精度が悪くなる
>- `N`が大きいと時間がかかる．

### マンデルブロ集合を作る
適当な範囲から複素数をとってきて判定し`True`なら配列`mandelbrots`にいれる．
```python
# パラメータ設定
N = 50 # 判定時のループ回数の設定
res = 200 # 解像度

# 候補点を生成
reals = np.linspace(-2, 0.6, num=res) # 実軸方向のメッシュ
imags = np.linspace(-1.1, 1.1, num=res) # 虚軸方向のメッシュ

# 探索実行
mandelbrots = []
for x, y in itertools.product(reals, imags): # 格子点上の(x, y)に対してループ
    c = np.complex(x, y) # 複素数の候補
    if judge_mandelbrot(c, N): # 判定
        mandelbrots.append([c.real, c.imag]) # 判定がTrueならマンデルブロ集合に加える

mandelbrots = np.array(mandelbrots) # 型変換
print(mandelbrots.shape) # 結果の数を確認
```

>補足
>- `res`が小さいと荒い画像ができる．
>- `res`が大きいと時間がかかる．

### 図の作成
```python
# 描画する点の大きさを設定
marker_size = 0.5

fig, ax = plt.subplots(figsize=(5,5), facecolor='k')
ax.scatter(mandelbrots[:,0], mandelbrots[:,1], s=marker_size, color = 'w')
ax.set_facecolor('k')
ax.set_aspect('equal')
ax.get_xaxis().set_visible(False)
ax.get_yaxis().set_visible(False)
```

### （発展）アニメーションの作成
```python
d = 50

fig, ax = plt.subplots()
def update(i):
    if d*i + d > len(mandelbrots):
        z = mandelbrots[d*i:]
    else:
        z = mandelbrots[d*i: d*i + d]
    ax.scatter(z[:, 0], z[:, 1], s=marker_size)
    ax.set_facecolor('k')
    ax.set_aspect('equal')
    ax.get_xaxis().set_visible(False)
    ax.get_yaxis().set_visible(False)
    ax.set_xlim([-2, 0.6])
    ax.set_ylim([-1.1, 1.1])

anim = animation.FuncAnimation(fig, update, frames=len(mandelbrots)//d + 1, interval=20)
rc('animation', html='jshtml')
anim
```

>補足
>- `d`が小さ過ぎると時間がかかり過ぎて終わらなくなる．

## 演習
以下のパラメータを変えながらマンデルブロ集合をプロットします．

### パラメータ

|パラメータ|説明|推奨値|
|:---|:---|---:|
| `N` | 判定時のループ |50|
| `res` | 解像度 |200|
| `marker_size` | プロットする点の大きさ |0.5|
| `d`| （発展）アニメーション時にまとめてプロットする点の数 |50|

次の手順を繰り返します．
1. `N`, `res`を設定して，「マンデルブロ集合を作る」を実行する．
2. `marker_size`を設定して，「図の作成」を実行して図を確認する．
3. （発展）`d`を設定して，「アニメーションの作成」を実行する．

### 作図例
![マンデルブロ集合作図](/assets/img/programming/mandelbrot.png)

<!-- ![マンデルブロ集合描画アニメーション](/assets/img/mandelbrot_colors.gif) -->

## まとめ
- 簡単なコードでマンデルブロ集合の作図を行いました．
- パラメータの調整で精度と時間のトレードオフを体験しました．
- アニメーションも作ったのでPythonによる作図が一通り学べました．

## 参考
- [wikipedia, 2021-08-17](https://ja.wikipedia.org/wiki/%E3%83%9E%E3%83%B3%E3%83%87%E3%83%AB%E3%83%96%E3%83%AD%E9%9B%86%E5%90%88)
- [GOOGLE DOODLE, 2021-08-17](https://www.google.com/fbx?fbx=mandelbrot_explorer&hl=ja)
- [Google Colaboratoryの使い方, 2021-08-17](https://qiita.com/yamaza-h/items/503d175e8da349cbcb6c)
