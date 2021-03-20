---
layout: post
title:  "Reactで画像のLazyLoad"
date:   2020-08-17 14:06:00 +0900
dir: /programming/
tags: React
---
### 目的
ReactでSeoのために画像をスクロールに沿って遅延読み込みしたい．

### 実装
ライブラリ : [React Lazy Load Image Component](https://www.npmjs.com/package/react-lazy-load-image-component)を使いました．

#### 特筆事項
- SSR(Server Side Rendering)にも対応．
- デフォルトでもちゃんとLazyLoadしてくれる．
- `props`
  - `afterload`, `beforeload`:読み込み前後のcallbackを指定できる．
  - `effect`:(string) blurなどの表示のスタイルを変更できる．
  - `threshold`: (number) で読み込み始める域値(画像の画面に見えている部分の長さ)を指定できる(pixel指定)．
- 詳しくはライブラリのページ

#### 使い方
インストール
```
$ yarn add react-lazy-load-image-component
```
使用例
- `<img />`と同じ`props`を渡せる．
- その他`props`で読み込み方を調整．

```jsx
import React from 'react';
import { LazyLoadImage } from 'react-lazy-load-image-component';

const SomeConponent = () => (
  <div>
    ...
    <LazyLoadImage
    // <img />のpropsと同様
      height={height}
      src={src}
      width={width}
      // その他props
      afterload={() => console.log('loaded!')}
      delayTime={300}
      threshold={100}
    />
    ...
  </div>
);
 
export default SomeConponent;
```