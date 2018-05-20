# コンパイルの仕方（dylibのリンク付き）

```
$ cd src/
$ gcc -o NeCab main.c -lm helloworld.dylib
```

## 実行確認

```
$ cd src/
$ ./NeCab
Hello World!
```

## `implicit declaration of function`ワーニング

コンパイルすると以下の警告が出ても問題ありません。これは、ソースの中で定義されていない関数 `hello` が使われているためです。この関数はリンクされたライブラリ内で定義されています。

```
$ gcc -o NeCab main.c -lm helloworld.dylib
main.c:2:9: warning: implicit declaration of function 'hello' is invalid in C99
      [-Wimplicit-function-declaration]
        return hello();
               ^
1 warning generated.
```

ワーニングがきもち悪い場合、回避策としては `int main(){...}` の定義より前に、プロトタイプ宣言として `int hello();` を宣言します。
