macOS HighSierra (OSX 10.13.4) で ダイナミック・ライブラリ（`.dylib`）を作成・利用するにあたり、参考にしたドキュメント一覧。

- Apple 公式の基本リファレンス
    - [Dynamic Library Programming Topics](https://developer.apple.com/library/content/documentation/DeveloperTools/Conceptual/DynamicLibraries/000-Introduction/Introduction.html) @ developer.apple.com
- Dylib内のシンボル一覧を出力
    - [How to print a list of symbols exported from a dynamic library](https://stackoverflow.com/questions/4506121/how-to-print-a-list-of-symbols-exported-from-a-dynamic-library) @ Stackoverflow
- Dynamic **Link** ライブラリと Dynamic **Load** ライブラリの違い
    - [.soや.dylibや.aファイル、共有ライブラリなどについて調べてみた](http://d.hatena.ne.jp/kanonji/20121018/1350538932) @ kanonjiの日記
- `hello world` の `.dylib` を作るのに参考にしたサイト
    - [OSXのdylibを作ってみる](http://taichino.com/programming/2533#more-2533) @ taichino.com
- 対象となるダイナミック・ライブラリに関する諸情報を取得する
    - [macOSのコマンドラインアプリでdylibをよろしく扱う方法](https://qiita.com/omochimetaru/items/21d662b8df8bce1bc5ca) @ Qiita
    - [関数が定義されているか確認する](https://qiita.com/edo_m18/items/aa6cb84c0456fc6ce5c0) @ Qiita
- 本家の MeCab のソースコード
    - [https://github.com/metaps/mecab/blob/master/ext/mecab/mecab.h](https://github.com/metaps/mecab/blob/master/ext/mecab/mecab.h)
- 別ディレクトリにあるユーザ作成の `.dylib` が絶対パスで指定できない問題
    - [@clang チャンネル](https://discord.gg/C8Pu95u) @ Discord

## 未整理

- [dynamic library の OS Xの補足](https://qiita.com/false-git@github/items/cb4528701752f76cfaa7) @ Qiita

