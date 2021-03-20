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
int = 1
f'i = {int}'
=> i = 1
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
    print(f'{i}: {value}')
```

<!-- ### 参考
### 注意 -->