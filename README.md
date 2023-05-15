# Dart-Sass-tutorial

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

v18.16.0

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
    "sass": "^1.62.1"
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

または、

```sh
% npx sass --watch sass:css
```

```sh
% npx sass --watch assets/sass:css
```

`npx sass --watch sass:css` の解説

`npx`とは node package executerの略でパッケージの実行ツールです。 npmとの違いはインストールされてないパッケージでも自動的に探してインストールして実行してインストールしたパッケージの削除をします。

npx sass `--watch` sassファイルの更新を監視して変更と同時にcssファイルにコンパイルします。

npx sass --watch `sass:css` :を挟んで、左辺は、sassファイルがあるディレクトリ:右辺は、cssファイルを保存するディレクトリ

ソースマップ(.mapファイル)を作成しないようにするには、

```sh
% npx sass --watch --no-source-map sass:css
```

監視を停止するには、 Ctrl-C　で停止することができる

## css基礎

```css
.セレクター {
    プロパティ: 値;
}
```

## まずはindex.htmlを記載する

```html:index.html
<!DOCTYPE html>
<html lang="ja">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="./css/style.css">
</head>

<body>
    <div class="card">
        <div class="thumbnail">
            <img src="./img/photowelcome-min.png" alt="welcome">
        </div>
        <div class="text">
            <p class="date">2023.04.13</p>
            <p class="title">A Coffee</p>
            <p class="description">
                コーヒーショップにある、模様を撮影しました。
                落ち着いた店内で、ゆっくり過ごすことができました。
            </p>
        </div>
    </div>
</body>

</html>
```

```css
@charset "UTF-8";
.card {
  width: 200px;
  padding-bottom: 20px;
  border: 1px solid #000;
  border-radius: 10px;
  color: #333;
  /* ここに下層のセレクタを記載する */
}
.card .thumbnail {
  margin: 0 0 20px;
}
.card .thumbnail img {
  width: 100%;
  height: auto;
  border-top-right-radius: 10px;
  border-top-left-radius: 10px;
}
.card .text {
  padding-left: 1em;
  padding-right: 1em;
}
.card .text .date {
  font-size: 16px;
  color: #777;
}
.card .text .title {
  font-size: 20px;
  font-weight: 700;
  margin: 12px 0 0;
}
.card .text .description {
  font-size: 14px;
  margin: 12px 0 0;
  font-feature-settings: "palt";
  line-height: 1.7;
  letter-spacing: 0.07em;
}
```

普通にcssをかくと、セレクターの終わりは中かっこの終わりに新しいセレクターを記載しています。

38行でした。

## sass 解説

1. ネスト(入れ子)の書き方

親の中かっこの中に下層のスタイルを描くことができます。

親のセレクターを毎回記載する必要がなくなります。

結果コード量の記載が少なくなります。

```sass
.card {
    width: 200px;
    padding-bottom: 20px;
    border: 1px solid #000;
    border-radius: 10px;
    color: #333;
    /* ここに下層のセレクタを記載する */
    .thumbnail {
        margin: 0 0 20px;
        img {
            width: 100%;
            height: auto;
            border-top-right-radius: 10px;
            border-top-left-radius: 10px;
        }
    }
    .text {
        padding-left: 1em;
        padding-right: 1em;
        .date {
            font-size: 16px;
            color: #777;
        }
        .title {
            font-size: 20px;
            font-weight: 700;
            margin: 12px 0 0;
        }
        .description {
            font-size: 14px;
            margin: 12px 0 0;
            font-feature-settings: "palt";
            line-height: 1.7;
            letter-spacing: 0.07em;
        }
    }
}
```

sass　で記載すると、37行になりました。

2. `&`(アンパサンド)の使い方

親のセレクタを参照することができる、書き方です。

擬似クラス(:hover)などに使われます。

先ほどのcardに詳細はこちらボタンを作成しましょう。

```index.html
    <div class="card">
        <div class="thumbnail">
            <img src="./img/photowelcome-min.png" alt="welcome">
        </div>
        <div class="text">
            <p class="date">2023.04.13</p>
            <p class="title">A Coffee</p>
            <p class="description">
                コーヒーショップにある、模様を撮影しました。
                落ち着いた店内で、ゆっくり過ごすことができました。
            </p>
        </div>
        <button class="button">詳細はこちら</button>
    </div>
```

```sass
.card {
    width: 200px;
    padding-bottom: 20px;
    border: 1px solid #000;
    border-radius: 10px;
    color: #333;
    /* ここに下層のセレクタを記載する */
    .button {
        color: white;
        background-color: #3952cd;
        border-radius: 5px;
        border-width: 1px;
        margin: 0 auto;
        display: block;
        &:hover{
            background: aqua;
        }
    }
    .button& {
      background-color: yellow;
    }
}
```

```css
card .button {
  color: white;
  background-color: #3952cd;
  border-radius: 5px;
  border-width: 1px;
  margin: 0 auto;
  display: block;
}
.card .button:hover {
  background: aqua;
}
```

また、セレクターの右横にもアンパサンドをつけることができます。

```sass
    .button {
        color: white;
        background-color: #3952cd;
        border-radius: 5px;
        border-width: 1px;
        margin: 0 auto;
        display: block;
        &:hover{
            background: aqua;
        }
    }
    .button & {
        background-color: yellow;
      }
```

```css
.button .card {
  background-color: yellow;
}
```

親セレクターを右に記載することができます。

親のセレクターがネストされていた場合、その上のセレクターも参照されます。

headerタグにある.button などに使えます。

3. 変数を使う

変数は、スタイルシート全体で共通利用したい部分をパーツとして利用します。
color や、font-family などに使うことができ、Sassの変数名は、 $変数名: 値;で宣言します。
あとは、$変数名を使いたい部分に記載するだけです。

```sass
$font-stack: Helvetica, sans-serif;
$primary-color: #333;
$secondary-color: #777;
$border-color: #000;
$buttonbk-color: #3952cd;
$buttonhr-color: aqua;
$buttonamp-color: yellow;
$white-color: white;
$size: 200px;
```

以上を先ほどのcardが入ったstyle.scss に追加しましょう。

```sass
body {
    font: 100% $font-stack;
    color: $primary-color;
}

.card {
    width: $size;
    padding-bottom: 20px;
    border: 1px solid $border-color;
    border-radius: 10px;
    color: $primary-color;
    /* ここに下層のセレクタを記載する */
    .thumbnail {
        margin: 0 0 20px;
        img {
            width: 100%;
            height: auto;
            border-top-right-radius: 10px;
            border-top-left-radius: 10px;
        }
    }
    .text {
        padding-left: 1em;
        padding-right: 1em;
        .date {
            font-size: 16px;
            color: $secondary-color;
        }
        .title {
            font-size: 20px;
            font-weight: 700;
            margin: 12px 0 0;
        }
        .description {
            font-size: 14px;
            margin: 12px 0 0;
            font-feature-settings: "palt";
            line-height: 1.7;
            letter-spacing: 0.07em;
        }
    }
    .button {
        color: $white-color;
        background-color: $buttonbk-color;
        border-radius: 5px;
        border-width: 1px;
        margin: 0 auto;
        display: block;
        &:hover{
            background: $buttonhr-color;
        }
    }
    .button & {
        background-color: $buttonamp-color;
      }
}
```

結果を確認してみましょう。

4. モジュール

sassでは、部品、役割などの特定の機能をファイル単位で分けてパーシャルという
アンダースコアをつけたファイルに分けて開発します。
最終的に、style.sassでひとまとまりにモジュール化します。

_base.scss




```sass
_mixin.scss
_header.scss
_footer.scss

style.scss
```

など。
