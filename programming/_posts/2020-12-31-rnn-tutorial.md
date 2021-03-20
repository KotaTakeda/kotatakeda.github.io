---
layout: post
title: "RNN入門"
date: 2020-12-31 17:00:00 +0900
dir: /programming/
tags: '機械学習'
---

### 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [コード](#コード)
- [まとめ](#まとめ)
- [参考](#参考)

### Key word
- RNN, 時系列解析
- Python, Google Colab

### はじめに
RNNを使ってみようということで(理論はそっちのけで)sin波の推定を行うことを目的とします．
環境はGoogle Colaboratoryです．

### コード
必要なライブラリをimport

```python
import tensorflow.keras
from keras import  models, layers
import numpy as np
import matplotlib.pyplot as plt
```

#### 時系列データの生成
ノイズ入りのsin波を生成します．
```python
# sin波を生成 in: dt, sample_size, out: sin_series(sample_size)
def generate_sin(dt=0.01, sample_size=100):
    return np.sin(2.*np.pi*np.linspace(0, dt*(sample_size-1), sample_size))

# ノイズを加える 正規分布N(0, 0.1)に従うノイズを加える
def noised_series(series, std=0.1):
    return series + np.random.normal(loc=0, scale=std, size=len(series))

clean_sin = generate_sin(sample_size=500)

noised_sin = noised_series(clean_sin)

# 生成したデータの可視化
plt.plot(clean_sin, label='clean')
plt.plot(noised_sin, label='noised')
plt.legend()
```

test-train split
データを訓練用とテスト用に分ける
```python
train_ratio = 0.7
train_size = int(len(noised_sin)*train_ratio)
train = noised_sin[:train_size]
test = noised_sin[train_size:]

print(f'train_size: {train_size}')
```
`=> train_size: 350`


データをRNN用に変換
```python
def convert_data_for_RNN(raw_data, delay=25):
    features = np.array([raw_data[n:n+delay] for n in range(len(raw_data)-delay)]).reshape(-1, 25,1)
    targets = raw_data[delay:].reshape(-1,1,1)
    return features, targets

train_features, train_targets = convert_data_for_RNN(train)
test_features, test_targets = convert_data_for_RNN(test)
train_features.shape, train_targets.shape
```
`=> ((325, 25, 1), (325, 1, 1))`


#### モデルの構築
```python
delay = 25 # 時間遅れstep
out_size = 1 # targetのsize
n_hidden = 20 # 中間層のノード数

model = models.Sequential(name='RNN')
model.add(layers.SimpleRNN(n_hidden, input_shape=(delay, out_size), return_sequences=False))
model.add(layers.Dense(out_size))
model.compile(loss='mean_absolute_error', optimizer='Adam')
model.summary()
```
<!-- 
Model: "RNN"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
simple_rnn_10 (SimpleRNN)    (None, 20)                440       
_________________________________________________________________
dense_10 (Dense)             (None, 1)                 21        
=================================================================
Total params: 461
Trainable params: 461
Non-trainable params: 0
_________________________________________________________________ -->

学習
```python
model.fit(train_features,
          train_targets,
          batch_size=20,
          epochs=10,
          validation_split=0.3,
          )
```
`batch_size`や`epoch`, `validation_split`の値は適当です．

fittingの確認
```python
train_predict = model.predict(train_features)

plt.plot(train_predict, label='train predict')
plt.plot(train_targets[:, 0,0], label='train targets')
plt.legend()
```
train dataをpredictしています．
MSEは0.0156

未来の予測
```python
test_predict = model.predict(test_features)

plt.plot(test_predict, label='test pred')
plt.plot(test_targets[:,0,0], label='test target')
plt.legend()

model.evaluate(test_features, test_targets)
```
test dataをpredictしています．
MSEは0.0171

### 考察
テストデータに対する予測のRMSEは0.1309となり．ノイズの標準偏差0.1と同程度になりました．ある程度予測できているようです．

#### パラメータ
チューニングの余地があるパラメータは
- model
  - `delay`
  - `n_hidden`
  - `dropout`や`regularity`など今回使わなかったもの
- 学習
  - `batch_size`
  - `epoch`
  - `validation_split`

### まとめ
- kerasのSimpleRNNを用いてノイズのあるsin波の予測を行いました．
- RNN用にデータを変換するところはテクニカルですが，kerasを使うことで簡単に学習まで行うことができました．


### 参考
- [初心者のRNN(LSTM):Kerasで試してみる](https://qiita.com/sasayabaku/items/b7872a3b8acc7d6261bf): 適当にパラメータを決める際の参考にしました．