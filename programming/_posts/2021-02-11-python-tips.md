---
layout: post
title: "Python Tips"
date: 2021-02-11 17:22 +0900
dir: /programming/
tags: "Python"
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

#### 数値計算
これはpythonに特有ではない．
解析解と数値解のtime indexを合わせる．

```python
t_arr = np.linspace(0, Tstep*dt, Tstep+1) % 時間index
results = np.zeros(Tstep + 1) % 数値解の記録用配列
```

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

#### numpy array結合
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
<!-- ### 参考
### 注意 -->
