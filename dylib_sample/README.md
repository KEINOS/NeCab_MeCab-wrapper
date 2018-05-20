# helloworld.dylib の作成

"Hello World!" を出力するだけのダイナミック・ライブラリ。

本体（src/）からのライブラリ読み込みのテスト用です。

- ソースコード： [helloworld.c](helloworld.c)
- コンパイル済： helloworld.dylib

## コンパイルの仕方

```
$ cd dylib_sample
$ gcc -dynamiclib -o libhelloworld.dylib helloworld.c
```
