macOS HighSierra (OSX 10.13.4) で ダイナミック・ライブラリ（`.dylib`）を作成・利用するにあたり、参考にしたドキュメント一覧。

- Apple 公式の基本リファレンス
    - [Dynamic Library Programming Topics](https://developer.apple.com/library/content/documentation/DeveloperTools/Conceptual/DynamicLibraries/000-Introduction/Introduction.html) @ developer.apple.com
- Dynamic **Link** ライブラリと Dynamic **Load** ライブラリの違い
    - [.soや.dylibや.aファイル、共有ライブラリなどについて調べてみた](http://d.hatena.ne.jp/kanonji/20121018/1350538932) @ kanonjiの日記
- `hello world` の `.dylib` を作るのに参考にしたサイト
    - [OSXのdylibを作ってみる](http://taichino.com/programming/2533#more-2533) @ taichino.com
- 対象となるダイナミック・ライブラリに関する諸情報を取得する
    - [macOSのコマンドラインアプリでdylibをよろしく扱う方法](https://qiita.com/omochimetaru/items/21d662b8df8bce1bc5ca) @ Qiita