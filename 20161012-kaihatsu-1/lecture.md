# 開発入門1

---

## 最初に

### Windows

```sh
pacman -Sy pacman
pacman -S nano
```

### macOS

```sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

---

## 使用コマンド一覧

- `pwd`: 現在の作業ディレクトリを表示
- `ls`: 現在の作業ディレクトリのファイルを一覧表示
- `date`: 日時を表示
- `cd`: 作業ディレクトリ移動
- `.`, `..`, `~`, `/`: 特殊なパス
- `mkdir`: ディレクトリを作成
- `touch`: ファイルを作成
- `rm`: ファイルを削除
- `nano`: ファイルを編集（テキストエディタ）
- `cat`: ファイルの中身を出力
- `head`: ファイルの先頭を出力
- `rm`: ファイルを削除
- `*`, `?`, `[]`, `[!]`: ワイルドカード
- `cp`: ファイルをコピー
- `mv`: ファイルを移動・名前を変更
- `curl`: URLからインターネット上のファイルの中身を出力
- `>`, `>>`: リダイレクト
- `grep`: ファイル内の文字列を検索
- `|`: パイプライン

---

## どうしてCUI？

- あるツールをプログラムを書いて作ることを考える
- CUIのツールとGUIのツール、どちらのほうが作りやすそう？

---

## `pwd`: ここはどこ？
- 現在いる **作業ディレクトリ** を表示
- GUIファイルエクスプローラにおいても「ここはどこ？」は重要な情報

## `ls`: ここに何がある？
- 今いる作業ディレクトリにあるファイルのリストを表示

## `date`: いま何時？
- 使わないと思うけど一応こういうのもあります

---

## `echo`: オウム返し
- `echo hi`: `hi` と出力される
- `echo 最高`: `最高` と出力される

## `cd`: 別の作業ディレクトリに移動してみよう
- `cd Downloads`: `Downloads`というディレクトリに移動
- `cd Downloads/tutorial`: `Downloads`の中の`tutorial`というディレクトリに移動
- `cd "oooh nice"`: `oooh nice`というディレクトリに移動
  - スペースが空いている場合はQuoteで囲まなければならない

## `.`, `..`, `~`, `/`: 特殊なパス一覧
- `.`: 現在の作業ディレクトリ
- `..`: 一つ上のディレクトリ
- `~`: ホームディレクトリ
  - ホームディレクトリは（たぶん）シェルを立ち上げて一番最初にいるディレクトリです。ユーザ設定とかを保存する
- `/`: ルートディレクトリ
  - ルートディレクトリは一番上のディレクトリ、親を持たないディレクトリを指します

## 絶対パス、相対パス
- シェルの操作は、原則作業ディレクトリからの **相対パス** でパスを入力する
  - 例えば、作業ディレクトリが `/home/yutaka` であれば、 `Downloads` という相対パスは、絶対パスでは `/home/yutaka/Downloads` と表す
  - `/home/yutaka` に居る場合、 `Downloads` と `/home/yutaka/Downloads` は全く同じ場所を示す

## `mkdir`: ディレクトリを作ろう
- `mkdir test`: `test`というディレクトリを作成
- `mkdir Downloads/001`: `Downloads` ディレクトリの中に `001` というディレクトリを作成

## `touch`: ファイルを作ろう
- 空の、なにも内容のないファイルができます
- `touch note.txt`: `note.txt` というファイルを作成
- `touch 001/hoge.txt`: `001` ディレクトリの中に `hoge.txt` というファイルを作成

---

## `nano`: ファイルを編集しよう
- `nano note.txt`: `note.txt` を編集
 	- カーソルのある位置にテキストを入力できる
  - 画面下に操作説明があるからカンタン！
  - Ctrl+O でセーブ、ファイル名を決めて Enter で保存
  - Ctrl+X で終了、変更がある場合は保存するか聞かれる

## エディタは他にもたくさんあるよ
- CUI上で動くものの中では、 `vim` と `emacs` が代表的
- `nano` は初心者用として親しまれています
- GUIが使える環境であれば、当然GUIのエディタを使えばオッケー。 [Atom](https://atom.io/) や [Visual Studio Code](https://code.visualstudio.com) が定番です

---

## `cat`: ファイルの中身を出力してみる
- `cat note.txt`: `note.txt` というファイルの中身を出力する

## `head`: ファイルの頭だけ見てみる
- `head note.txt`: `note.txt` というファイルの先頭部分を出力する
  - デフォルトでは10行
- `head -n 3 note.txt`: `note.txt` というファイルの先頭3行を表示する
- `head -c 512 note.txt`: `note.txt` というファイルの先頭512バイト（文字）を表示する
- `tail` もあるよ

## `rm`: ファイルを消そう
- ゴミ箱には入らず、 **完全に消える** 、しかも **確認なし** なので注意！
- `rm note.txt`: `note.txt` というファイルを削除
- `rm -r Downloads`: `Downloads` というフォルダごと削除

## `*`, `?`, `[]`, `[!]`: ワイルドカード
- `rm temp*`: `temp` から名前が始まるファイルをすべて削除
- `rm *.txt`: 拡張子が `.txt` のファイルをすべて削除
- `rm test?.txt`: `?` は任意の1文字に当てはまる
- `rm test[2345].txt`: `[2345]` は `2`, `3`, `4`, `5` のいずれか1文字に当てはまる
- `rm test[!123].txt`: `[!123]` は `1`, `2`, `3` 以外のいずれか1文字に当てはまる

## `cp`: ファイルをコピーしよう
- `cp note.txt note2.txt`: `note.txt` というファイルを `note2.txt` という名前でコピー
- `cp -r Downloads backup`: `Downloads` というディレクトリを `backup` という名前でコピー

## `mv`: ファイルを移動・名前を変更しよう
- `mv note.txt letter.txt`: `note.txt` というファイルの名前を `letter.txt` に変更
- `mv note.txt Downloads/note.txt`: `note.txt` を `Downloads` というディレクトリに移動
- ディレクトリを移動する場合も、 `mv` では `-r` オプションはいらない

---

## `curl`: インターネット上のデータを見てみよう
- `curl http://example.com`: http://example.com の中身を出力

## `>`, `>>`: リダイレクト
- プログラムの出力をファイルに保存する
- `ls > list.txt`: `ls` の出力を `list.txt` に保存
- `curl http://example.com > index.html`: http://example.com の中身を `index.html` に保存
- `date >> date.txt`: `date` の出力を `date.txt` に追記 （末尾に追加）

## `grep`: 文字列を検索してみよう
- `grep awesome note.txt`: `note.txt` から `awesome` が含まれる行を検索
  - `awesome` が含まれる行を出力する
- `grep -i awesome note.txt`: 大文字小文字を区別しない
- `grep -n awesome note.txt`: 行番号付きで出力する
- `grep -r awesome .`: 現在の作業ディレクトリ全体を対象として検索
- `grep -inr awesome .`: オプションはこのように複数指定できる

## `|`: パイプライン
- プログラムの出力を他のプログラムにリレーする
- `curl http://example.com | grep example`: http://example.com の中身から `example` が含まれる行を検索

---

## 発展

### 変数
- `hoge="stal cool"`: `hoge` という変数に `stay cool` という文字列を代入
- `echo $hoge`: `hoge` という変数の中身を出力
- `echo $hoge" bro"`: `stay cool bro`
  - 文字列連結は気持ち悪い
- `echo $PATH`: `PATH` 変数の中身を出力
  - `$PATH` に記述されたディレクトリに入っているモノには、そのディレクトリからの相対パスを記述するだけでアクセスできる

### `for` 文もあるよ
- `for i in {1..10}; do echo $i; done`: `1` から `10` を順に出力
- `for file in *.txt; do mv $file ${file%.txt}.md; done`
  - ググって覚える（とても重要）
  - 今は「繰り返し処理もできるよ」ということを覚えて

---

## あわせてどうぞ

### 他にはどんなコマンドがある？
- インターネットにはたくさんプログラムがあります
  - `ncdu`: ディレクトリ内の各ファイルの容量をわかりやすく確認
  - `convert`（ImageMagick）: 画像を変換したり処理するのに使う
  - `ffmpeg`: 動画を変換したりトリミングしたりできる
  - `sl`, `cowsay`: ネタプログラム
  - `python`, `ruby`, `node`, `lua`...: 各種プログラミング言語のインタプリタ。次回説明します
- おもしろいコマンドを先輩に聞いてみよう！

### コマンドは覚えなきゃダメ？
- ググりながら覚えれば良い
  - コマンド操作に慣れていても、知らないコマンドは知らないし、忘れたコマンドは忘れてる
  - リダイレクトやパイプラインなどの高度なテクニックも必要なときにググるうちに覚える

### わかりやすいスライド
- 農工大MCCの [icchyr](https://twitter.com/icchyr) さんのスライドがとても良かったです  
  http://www.slideshare.net/icchyr/ss-52341962

### Bash on Windows
- Windows 10 Anniversary Updateで追加された新機能
  - Msys2より断然オススメ
  - Anniversary Updateが必要なため、今回は紹介しませんでした
- Linuxの各種コマンドがWindowsでも使える
- 詳しくは http://qiita.com/Aruneko/items/c79810b0b015bebf30bb などをご覧ください

### かっこいいシェル
- 使っていくうちにシェルがどんどんカッコ良くなる
- カッコいいシェル一覧  
  https://gyazo.com/collections/faf675ee9a69c449e55bb51bb88dbefb
