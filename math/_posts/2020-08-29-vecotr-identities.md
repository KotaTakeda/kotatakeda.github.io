---
layout: post
title: "ベクトルの公式"
description: "物理や流体関係で使うベクトル，ベクトル解析の公式"
date: 2020-08-29 15:45:00 +0900
dir: /math/
tags: "公式"
---

## 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [公式](#公式)
- [参考](#参考)
<!-- - [注意](#注意) -->

## Key word
- ベクトル解析，偏微分方程式
- 流体力学，電磁気学

## はじめに
ベクトル解析など物理寄りの文脈で登場することの多いベクトルの公式を忘れないように書いておきます．

## 公式
随時更新します．

$ \vec{u}, \vec{v} : \mathbb{R}^3 \rightarrow \mathbb{R}^3 , \phi: \mathbb{R}^3 \rightarrow \mathbb{R} $．
- $ \nabla \cdot (\nabla \times \vec{u}) = 0 $
- $ \nabla \times (\nabla \phi) = \vec{0} $
- $ \nabla (\vec{u} \cdot \vec{v}) = (\vec{u} \cdot \nabla)\vec{v} + (\vec{v} \cdot \nabla)\vec{u} + \vec{u} \times (\nabla \times \vec{v}) + \vec{v} \times (\nabla \times \vec{u}) $
- $ \nabla \times (\vec{u} \times \vec{v}) = \vec{u}(\nabla \cdot \vec{v}) - \vec{v}(\nabla \cdot \vec{u}) + (\vec{v} \cdot \nabla)\vec{u} - (\vec{u} \cdot \nabla)\vec{v} $
- $ \frac{1}{2} \nabla(\vec{u} \cdot \vec{u}) = (u \cdot \nabla)\vec{u} + \vec{u} \times (\nabla \times \vec{u}) $
- $ \nabla \times (\nabla \times \vec{u}) = \nabla(\nabla \cdot \vec{u}) - (\nabla \cdot \nabla) \vec{u} $

[pdfリンク](/math/pdf/vector_identities.pdf)
## 参考
pdfリンクにあります．
<!-- ## 注意 -->
