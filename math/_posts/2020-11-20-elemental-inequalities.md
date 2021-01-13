---
layout: post
title: "初等不等式まとめ"
date: 2020-11-20 15:20:00  +0900
dir: /math/
tags: '初等数学'
---
<!-- 開発用 -->
<script async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-AMS_CHTML"></script>
<script type="text/x-mathjax-config">
 MathJax.Hub.Config({
 tex2jax: {
 inlineMath: [["\\(","\\)"], ['$','$'] ],
 displayMath: [ ['$$','$$'], ["\\[","\\]"] ]
 }
 });
</script>

### 目次
- [Key word](#key-word)
- [はじめに](#はじめに)
- [まとめ](#まとめ)
- [参考](#参考)

### Key word
- 不等式

### はじめに
初等的な不等式の備忘録です．随時更新します．

### 不等式
#### 1. 2乗不等式(仮)
$ x^2 \ge 0 \hspace{2em} (\forall x \in \mathbb{R}) $

#### 2. 三角不等式
$ |x+y| \le |x| + |y| \hspace{2em} (\forall x,y \in \mathbb{C}) $

#### 3. 発展的三角不等式
$ p > 0 \Rightarrow |x+y|^p \le \max(1, 2^{p-1})(|x|^p + |y|^p) \hspace{2em} (\forall x,y \in \mathbb{C}) $


#### 4. 相加・相乗・調和不等式
$ \frac{2xy}{x+y} \le \sqrt{xy} \le \frac{1}{2}(x+y) $

#### 5. Bernoulliの不等式
$ \forall x > -1, r \in [0,1] \Rightarrow (1+x)^r \le 1 + rx, \hspace{2em} r \notin [0,1] \Rightarrow (1+x)^r \ge 1 + rx $

### まとめ
- 2乗不等式は自明ですが役に立つことがあり侮れないです．
- 三角不等式はよく使います．

<!-- ### 参考 -->
<!-- ### 注意 -->