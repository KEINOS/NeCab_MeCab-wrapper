# コンパイルの仕方（dylibのリンク付き）

以下の手順で本体の実行ファイルをコンパイルします。コンパイル時に `helloworld.dylib` をリンクさせていることに注意。将来的には `/usr/lib/libmecab.dylib` に置き換わります。

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

コンパイルすると以下の警告が出ても問題ありません。これは、ソースの中で定義されていない関数 `hello()` が使用されているためです。この `hello()` 関数はコンパイル時にリンクされたライブラリ内で定義されています。

```
$ gcc -o NeCab main.c -lm helloworld.dylib
main.c:2:9: warning: implicit declaration of function 'hello' is invalid in C99
      [-Wimplicit-function-declaration]
        return hello();
               ^
1 warning generated.
```

ワーニングがきもち悪い場合、回避策としては `int main(){...}` の定義より前に、プロトタイプ宣言として `int hello();` を宣言します。
