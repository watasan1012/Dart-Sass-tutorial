# sass-beginner

## .gitignoreファイルを作成してgit対象から外す

```sh
% echo ".DS_Store" >> .gitignore
```

.DS_Storeフォルダやファイルに関するmeta情報が格納されています。

さらに npm install で作成された　node_modules/ ディレクトリーを.gitignoreファイルに記載してgit対象から外します。

```json
.DS_Store

node_modules/
```

## vscode のメニューの日本語化

Command Palette　を表示する、shift + command + p

テキストボックスにlanguage と入れる

Configure Display Languageを選択

日本語を選択する

## vscode の分割表示

メニューバーにある、表示　>　エディターレイアウト > 3列　とか 3行とか

## Sass の基本

sassの公式サイトは、[sass-lang](https://sass-lang.com/)　です。

## Sass をセットアップする

1. ターミナルを起動する

プロジェクトのルートディレクトリを作成し、移動する。

```sh
% mkdir プロジェクトのルートディレクトリ名 && cd $_
```

プロジェクトのルートディレクトリ名は、自由に作成します。例えば、案件の名前とか

1. node.jsをインストールする

* nodeが入ってるか確認する

```sh
% node -v
```

v18.15.0

バージョンが記載されれば入っています。バージョンが表示されなかったらインストールされてません。以下公式URLからダウンロードするか

[https://nodejs.org/ja](https://nodejs.org/ja) よりインストールするか

バージョン管理ツールを使ってnodeをインストールする場合以下のツールを使う

1. nodebrew (macOS Linux)
2. nodenv (macOS)
3. nodist (Windows)
4. nvm (macOS Linux)
5. nvm-windows (windows)
6. Volta (Linux、Mac、Windows)

* サイトの雛形を作成する

index.htmlを作成する

```sh
% touch index.html
```

index.html をエディターで編集する

* sass ファイルを入れるフォルダーと、sassファイルを作成する

```sh
% mkdir sass && cd $_ && touch style.scss
```

* sassファイルのコンパイル

sassファイルは、htmlファイルから直性読み込むことはできません。
sassファイルをcssに変換する必要があります。
変換することをコンパイルといいます。

今回紹介するコンパイル方法は、2種類紹介します。

1. VS codeの拡張機能を使ってコンパイルします。
2. npmを使ってコンパイル

* VS Code を使ってコンパイルする

VS Code の左側メニューから拡張機能をクリックします。

リンク先からInstallをクリックしてインストールします。

▫️ [Sass(.sass onliy)](https://marketplace.visualstudio.com/items?itemName=Syler.sass-indented)

Sass 解説

構文を規則に応じて強調表示
自動的に、補完する構文を候補として表示
自動整形
ホバーによる情報の表示

などの機能が入っています。

これは、npmでコンパイルする場合でもVS code にインストールするといいと思います。

◽️ [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=glenn2223.live-sass)

Live Sass Compiler 解説

自動コンパイラ

ステータスバーにある watch Sass をクリックするとsassファイルをコンパイルする

ステータスバーがなかったら

VS Code　メニューバーにある表示　> 外観 > ステータスバー にチェックを入れる

* npm を使ったsassのインストール

package.json ファイルの作成(初期化作業)

プロジェクトのルートディレクトリで以下のコマンドを実行します。

```sh
% npm init -y
```

プロジェクトのルートディレクトリに、package.jsonが出現したことを確認します。

```json
Wrote to /Users/ユーザー名/work/sass-beginner/package.json:

{
  "name": "sass-beginner",
  "version": "1.0.0",
  "description": "## .gitignoreファイルを作成してgit対象から外す",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

* Dart Sassのインストール

```sh
% npm install --save-dev sass
```

package.json ファイルの　devDependencies　に"sass": "バージョン" が記載されていることを確認します。

```json
{
  "devDependencies": {
    "sass": "^1.62.0"
  }
}
```

* sassのコンパイルのための準備

1. package.json ファイルを修正する

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "sass": "sass --watch sass:css"
  },
```

のようにscriptsの中身を修正します。

* sassの実行方法

ターミナルより、プロジェクトのルートディレクトリで以下のコマンドを実行する

```sh
% npm run sass
```

監視を停止するには、 Ctrl-C　で停止することができる

## css基礎

```css
.セレクター {
    プロパティ: 値;
}
```

## sass 解説

