---
layout: post
title: "Python Tips"
date: 2021-02-11 17:22 +0900
dir: /programming/
tags: ["Python", "メモ"]
description: "Pythonに関するTipsをまとめています．"
---

### 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [まとめ](#まとめ)
- [参考](#参考)

### Key word
- Python

### はじめに
PythonについてのTipsを備忘録として書いていきます．
随時更新します．

### まとめ
#### 式展開
```python
i = 1
f'i = {i}'
# => i = 1
```
出力フォーマットも指定できる
```python
init_mon = 2
f'2017{init_mon:02d}'
# => 201702
```

#### dict
python 3.9以降，mergeできるようになった．
```python
a = {'a': 'A'}
b = {'b': 'B'}
a | b
=> {'a': 'A', 'b': 'B'}
```

<!-- #### 数値計算
これはpythonに特有ではない．
解析解と数値解のtime indexを合わせる．

```python
t_arr = np.linspace(0, Tstep*dt, Tstep+1) % 時間index
results = np.zeros(Tstep + 1) % 数値解の記録用配列
``` -->

#### enumerate
イテレート時にidxとvalueを両方使いたい時，`enumarate`を使う．
```python
for idx, value in enumerate(array):
    print(f'{idx}: {value}')
```

#### animation
animationをgifで保存する．（Imagemagic不要）
```python
# 例
import matplotlib.pyplot as plt
import matplotlib.animation as animation
from matplotlib.animation import PillowWriter # 明示的には使わない

...
# fig, animateを定義
...

anim = animation.FuncAnimation(fig, animate, frames=100)
anim.save('data/img/hmc_animation.gif', writer='pillow')
```

#### numpy
##### array結合
```python
a = np.zeros((10, 100, 1000))
b = a.copy()

c = np.vstack([a,b])
c.shape
# => (20, 100, 1000)

d = np.hstack([a,b])
d.shape
# => (10, 200, 1000)

e = np.block([a,b])
e.shape
# => (10, 100, 2000)
```

##### argsort
best3を選ぶときなどに使う．昇順で返される．
```python
target_arr = np.array([2, 7, 4, 9, 1, 5])
best_3idx = target_arr.argsort()[::-1][:3]
print(best_3idx)
# => [3, 1, 5]
```

##### reshapeの注意
目的に合わせて必要があれば転置と組み合わせる．
```python
data = np.arange(12)
print(data)

reshaped_data1 = data.reshape(4, 3)
print(reshaped_data1)

reshaped_data2 = data.reshape(3, 4).T
print(reshaped_data2)
```
結果
```
[ 0  1  2  3  4  5  6  7  8  9 10 11]
[[ 0  1  2]
 [ 3  4  5]
 [ 6  7  8]
 [ 9 10 11]]
[[ 0  4  8]
 [ 1  5  9]
 [ 2  6 10]
 [ 3  7 11]]
```

##### transpose
`.T`による転置の一般化．多次元配列の軸を入れ替える．


### 参考
- [Python Docs](https://docs.python.org/ja/3/)
- [matplotlib.animation.Animation](https://matplotlib.org/stable/api/_as_gen/matplotlib.animation.Animation.html#matplotlib.animation.Animation.save)
- [Numpy Docs](https://numpy.org/doc/stable/)
