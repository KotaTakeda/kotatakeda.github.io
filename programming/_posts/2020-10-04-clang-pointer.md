---
layout: post
title: "C言語のポインタまとめ"
date: 2020-10-04 15:02:00  +0900
dir: /programming/
tags: 'C言語'
---

### 目次
- [Keyword](#key-word)
- [はじめに](#はじめに)
- [ポインタ](#ポインタ)
- [関数の配列引数](#関数の配列引数)

### Keyword
- ポインタ，メモリ，アドレス
- 配列，関数，仮引数，型宣言

### はじめに
C言語のポインタ変数と関数の引数に配列を渡す際の注意ついてまとめます．

### ポインタ
#### コンピュータとメモリ
- コンピュータにはメモリ領域(以降メモリと書く．)にはアドレスが割り振られている．
- プログラムで変数を定義するとコンピュータ上のメモリがその変数に割り当てられます．

#### ポインタ変数
- 変数を定義する際に先頭に`*`をつけるとポインタ変数を宣言することができます．
- ポインタ変数にはメモリのアドレスを入れることができます．

#### 値の取得
普通の変数とポインタ変数の値の取得のまとめです．以下の例で考えます．

|変数|種類|値を取得|アドレスを取得(`&`)|アドレスに対応するメモリ上の値を取得(`*`)|
|---|---|---|---|---|
|`a`|`int`|`a`|`&a`|-|
|`p`|`int`へのポインタ|`p`(=> `a`のアドレス)|`&p` (=>ポインタ変数`p`に割り当てられたメモリのアドレス)|`*p` (=> `a`)|


例:
```c
#include <stdio.h>
int main(void) {
    int a = 3;
    int *p; // ポインタ変数

    printf("変数aの値 %d\n", a); //=> 2
    printf("変数aのアドレス %p\n", &a); //=> 0x7ffeeb0cb994(環境依存)

    p = &a; // アドレスの代入
    printf("p = &a\n");

    printf("ポインタ変数pのアドレス先の値 %d\n", *p); //=> 3
    printf("ポインタ変数pに代入されている値(アドレス) %p\n", p); //=> 0x7ffeeb0cb994
    printf("ポインタ変数p自体のアドレス) %p\n", &p); //=> 0x7ffeeb0cb988(環境依存)
    return 0;
}
```

### 関数の引数
C言語で関数の引数に配列を渡す際には注意が必要です．

#### 注意点
- 関数の引数としてそのまま配列を渡すことはできません．
- ポインタ変数として配列の始まりのメモリアドレスを渡します．
- 配列の長さの情報を渡すことはできません．

#### 実装
仮引数宣言の方法はいくつかありますが結果は同じです．[^pointer_pointer]
- `(int *arr)`: ポインタ変数として宣言．
- `(int arr[])`: 配列の形で宣言．
- `(int arr[131])`: 配列の長さも含めて宣言．131にはどんな自然数を入れても同じです．

```c
#include <stdio.h>

int pointer_arr_func(int *arr) {
    printf("arr = %p\n", arr); // 引数の値を取得．(=> アドレスが返ってくる．)
    printf("*arr = %d\n", *arr); // 引数の参照先の値を取得．
    printf("arr[0] = %d\n", arr[0]); // 引数の１つ目の値を取得．*arrと同様．
    return 0;
}

int arr_func(int arr[]) {
    printf("arr = %p\n", arr);
    printf("*arr = %d\n", *arr);
    printf("arr[0] = %d\n", arr[0]);
    return 0;
}

int main(void) {
    int arr[] = {10,20,30};

    printf("pointer_arr_func(int *arr) \n");
    pointer_arr_func(arr);

    printf("arr_func(int arr[]) \n");
    arr_func(arr);

    return 0;
}
```
実行結果:
```
/* =>
  pointer_arr_func(int *arr)
  arr = 0x7ffeeb0cb99c
  *arr = 10
  arr[0] = 10
  arr_func(int arr[])
  arr = 0x7ffeeb0cb99c
  *arr = 10
  arr[0] = 10
*/
```


### 参考
- [C言語：ポインタの概念の図解, 2020-10-04](https://cyzennt.co.jp/blog/2019/05/04/c%E8%A8%80%E8%AA%9E%EF%BC%9A%E3%83%9D%E3%82%A4%E3%83%B3%E3%82%BF%E3%81%AE%E6%A6%82%E5%BF%B5%E3%81%AE%E5%9B%B3%E8%A7%A3/) - 2020-10-04
- [配列型引数の奇妙な性質, 2020-10-04](https://9cguide.appspot.com/15-06.html#S3) - 2020-10-04
- [C言語型宣言の解説, 2020-10-04](https://qiita.com/omochimetaru/items/3b6b34036a1239603aff#%E9%96%A2%E6%95%B0%E3%83%9D%E3%82%A4%E3%83%B3%E3%82%BF%E3%81%AE%E8%AA%AD%E8%A7%A3) - 2020-10-04

### 注意
[^pointer_pointer]: `(int *arr[])`: とするとポインタの配列となるので意味が違います．
