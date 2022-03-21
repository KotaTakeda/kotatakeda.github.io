---
layout: post
title: "Runge現象"
date: 2022-02-18 18:33 +0900
dir: /math/
tags: ["数値解析", "UQ"]
description: "連続関数の多項式補間において，近似誤差は対象の関数と節点の取り方に依存します．Runge現象という近似誤差が発散する現象を紹介し，数値的に再現します．"
---

## 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [まとめ](#まとめ)
- [参考](#参考)

## Key word
- Lagrange補間多項式，Runge現象，Chebyshev多項式

## はじめに
連続関数の多項式補間において，近似誤差は対象の関数と節点の取り方に依存します．Runge現象という近似誤差が発散する現象を紹介し，数値的に再現します．

## まとめ
Colabolatoryにまとめました．
[Google Colabolatoryへ](https://colab.research.google.com/drive/17KSZ52UEkJkubNxpFtzM9XgfvCKfnOqG?usp=sharing)

## 参考
- Timothy John Sullivan. *Introduction to uncertainty quantification*, Springer, 2015
