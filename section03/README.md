# Webサービス勉強会2023 第3回

(2023/05/28)
HTMLとCSSについて、一緒に手を動かしながら簡単におさらいしましょう！

## 準備

環境構築が終わっていない人は[第1回資料](../section01/README.md)を基に構築してください。

1. Section03の追加を手元に取得します

WSL or Powershellを開いて（前回どちらでセットアップしたか思い出してください）

```bash
cd ~/2023-web
git pull
```

> No Such file or directory
とか言われたら以下を実行してください

2. 2023-webリポジトリをcloneします (optional)

```bash
cd ~
git clone git@github.com:kmc-jp/2023-web.git 
```

3. section03に移動します

```bash
cd ~/section03
```

4. サーバーを起動します

```bash
npm install
npm run dev
```

5. ブラウザからアクセスします

自動的に開くと思います

開かなければ <http://localhost:8080> にアクセス

Hello World!と表示されていればOKです！

いったんCtrl+Cで止めます

## HTMLの編集

1.  VSCodeの起動

~/2023-web/section03をターミナルで開いている状態で

```bash
code .
```
とするとVSCodeで開きます

2. index.htmlを探す

~/2023-web/section03/index.htmlです

![](../resources/2023-05-21_13h15_42.png)

3. 中身を見る

```html
<!DOCTYPE html>
<html lang="ja-JP">
  <head>
    <meta charset="utf-8">
    <link rel="stylesheet" href="style.css">
    <title>section 03 | 2023-web</title>
  </head>
  <body>
    <p>Hello World!</p>
  </body>
</html>
```

4. もう一度Webサーバーを起動

ターミナルに戻って

```bash
npm run dev
```

<http://localhost:3000> にアクセス

今日の講習会中はつけっぱにします

## CSSの基礎

今回はCSSについて基礎的事項をやります。

CSSはページのデザインについて指定するための言語です。
CSSでは、特定の要素に適用するスタイルをルールとして書き並べていきます。

とにかくまずは簡単に試してみます

`index.html` と同じ階層に `style.css` があるはずです。まだ中身は空です。

以下の内容を書いてみましょう

```css
p {
  color: red;
  font-size: 5em;
}
```

さて、ブラウザを開いてみましょう。見た目はどうなっていますか？　「Hello World!」の文字列がでかでかと真っ赤に表示されているでしょうか？

## CSSの基本構造

`p` の部分をセレクターといいます。
これは適用対象を指定するものです。今回は段落要素`p`の全てを指定しています。
複数`p`要素があればすべてに適用されます。試してみましょう

中かっこ`{ }`の中には、プロパティと値の組み合わせを書きます。
`color`や`font-size`の方がプロパティ、`red`や`5em`の部分を値です。
`プロパティ: 値;`という形で書きます。
1つのセレクターに対してプロパティとプロパティ値の組は複数記述することができます。


## index.htmlに要素を追加する

今のままだといじれる場所が少ないので、CSSの説明のために様々な要素を追加しておきます。
`index.html`を以下のように編集してください

```html
<!DOCTYPE html>
<html lang="ja-JP">
  <head>
    <meta charset="utf-8">
    <link rel="stylesheet" href="style.css">
    <title>section 03 | 2023-web</title>
  </head>
  <body>
    <h1>2023-web 第3回</h1>
    <p>2023-webの<span>第3回</span>です。</p>
    <p>これは<a href="https://kmc.gr.jp/">KMC</a>が開催する春プロジェクトの一つです。</p>

  </body>
</html>
```

## 指定方法

### [要素名による指定](https://developer.mozilla.org/ja/docs/Web/CSS/Type_selectors)

要素名を直接記述します。

```css
body {
  background-color: #030303;
  color: white;
}

a {
  color: #0c0c0c;
  text-decoration: none;
}
```

全ての要素に対してCSSを割り当てる場合は、`*`を記述します。

> [全称セレクター | MDN](https://developer.mozilla.org/ja/docs/Web/CSS/Universal_selectors)

```css
* {
  color: white;
}
```

### [idによる指定](https://developer.mozilla.org/ja/docs/Web/CSS/ID_selectors)

id名の前に`#`を付けて指定します。

```css
#alert {
  background-color: rgba(255, 192, 203, 0.3);
  display: inline-block;
  padding: 8px;
}
```

### [クラスによる指定](https://developer.mozilla.org/ja/docs/Web/CSS/Class_selectors)

クラス名の前に`.`を付けて指定します。

```css
.article-card {
  border-radius: 8px;
  box-shadow: 0 0 4px #7777;
  display: inline-block;
  padding: 8px;
}
```

### [属性による指定](https://developer.mozilla.org/ja/docs/Web/CSS/Attribute_selectors)

`[{属性名}={属性値}]`の形式で指定します。属性値が存在しない場合は、`[{属性名}]`の形式で指定します。<br>

```css
[aria-selected="true"] {
  background-color: #7773;
}
```

## 基本的なプロパティ

### テキスト色

テキストの色を指定するには、[`color`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/color)を使用します。

```css
p {
  color: black;
}
```

```css
p {
  color: #eee;
}
```

```css
p {
  color: rgb(34, 12, 64);
}
```

```css
p {
  color: rgba(34, 12, 64, 0.6);
}
```

### 背景色

要素の背景色を指定するには、[`background-color`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/background-color)を使用します。

```css
div {
  background-color: gray;
}
```

```css
div {
  background-color: rgb(255, 255, 128); 
}
```

```css
div {
  background-color: rgba(117, 190, 218, 0.5);
}
```

### 背景画像

### フォント
フォントの指定には、[`font-family`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/font-family)を使用します。

```css
.article {
  font-family: Gill Sans Extrabold, sans-serif;
}
```

フォントサイズの指定には、[`font-size`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/font-size)を使用します。

```css
.article {
  font-size: 12px;
}
```

```css
.article {
  font-size: 1.2em;
}
```

```css
.article {
  font-size: smaller;
}
```

### 太字・斜体

太字の指定には、[`font-weight`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/font-weight)を使用します。

```css
.title {
  font-weight: bold;
}
```

```css
.descriptions {
  font-weight: lighter;
}
```

斜体の指定には、[`font-style`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/font-style)を使用します。

```css
.article-main {
  font-style: italic;
}
```

### テキスト修飾

テキスト装飾の指定には、[`text-decoration`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/text-decoration)を使用します。

```css
.message-important {
  text-decoration: underline;
}
```

```css
.format-error {
  text-decoration: red wavy underline;
}
```

### 文字間隔

文字間隔の指定には、[`letter-spacing`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/letter-spacing)を使用します。

```css
.article {
  letter-spacing: .2rem;
}
```

```css
.article {
  letter-spacing: -1px;
}
```

### 行の高さ

行の高さの指定には、[`line-height`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/line-height)を使用します。<br>
`line-height`プロパティには、単位のない値を指定するのが好ましいとされています。

```css
.article {
  line-height: 2;
}
```

### 枠線

枠線の指定には、[`border`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/border)を使用します。

```css
.button-submit {
  border: 1px solid orange;
}
```

```css
.button-submit {
  border: thick double #32a1ce;
}
```

### 角丸

角丸の指定には、[`border-radius`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/border-radius)を使用します。

```css
.card {
  border-radius: 32px;
}
```

```css
.icon-header {
  border-radius: 50%;
}
```

```css
.logo {
  border-radius: 25% 10%;
}
```

### 透明度

要素全体の指定には、[`opacity`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/opacity)を使用します。<br>
このプロパティは子要素にも継承されます。<br>
背景色のみを透過したり、テキスト色のみを透過したりする場合は、背景色やテキスト色を透明度付きの色で指定してください。

```css
[aria-disabled="true"] {
  opacity: 0.5;
}
```

### 幅・高さ

```css
.square {
  height: 100px;
  width: 100px;
}
```

## もうちょっと詳しい話

### `div`と`span`、何が違うねん

これを見れば全てが分かります。

```html
<div>div</div>
<span>span</span>
```

```css
div {
  background-color: red;
  height: 100px;
  width: 100px;
}

span {
  background-color: aqua;
  height: 100px;
  width: 100px;
}
```
