---
layout: post
title:  "C言語のコンパイルまとめ"
date:   2020-08-16 14:30:00 +0900
dir: /programming/
---
### C言語のコンパイルについての備忘録(`gcc`による)

- `a.out`を作成.
```
$ gcc hello.c
```

- `a.out`を実行
```
$ ./a.out
```

- outファイルに名前を指定
```
$ gcc hello.c hello
// => hello ができる
```

- 複数ファイルから実行ファイルを作る

hello.c
```hello.c
#include <stdio.h>

void f() {
    printf("hello!\n");
}
```
main.c
```main.c
#include <stdio.h>
void f(){}

void main() {
  f();
 }
```
```
$ gcc main.c hello.c -o main
$ ./main
//=> hello!
```
このとき`duplicate symbol`エラーが出ることがある． [Duplicate Symbol? What?](https://samwho.dev/blog/duplicate-symbol-what/)

## 参考
[gcc コンパイルオプション備忘録](https://qiita.com/seriru13/items/c2f5192615162c4c3f47)

