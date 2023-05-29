# Webサービス勉強会2023 第3回

(2023/05/28)
CSSとJSについて、一緒に手を動かしながら簡単におさらいしましょう！

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
    <script src="script.js" defer></script>
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

<http://localhost:8080> にアクセス

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
    <meta charset="utf-8" />
    <link rel="stylesheet" href="style.css" />
    <script src="script.js" defer></script>
    <title>section 03 | 2023-web</title>
  </head>
  <body>
    <h1>2023-web 第3回</h1>
    <p>WebService勉強会2023の<span>第3回</span>です。</p>
    <p>
      これは<a href="https://kmc.gr.jp/">KMC</a
      >が開催する春プロジェクトの一つです。
    </p>
    <div class="projects">
      <h2>春プロジェクトの一覧</h2>
      <ul>
        <li>みんなでゲームを作る2023</li>
        <li>お絵かきプロジェクト2023</li>
        <li>自宅サーバー勉強会(Linux勉強会)2023</li>
        <li>Webサービス勉強会2023</li>
        <li>サウンドプログラミング講習会</li>
        <li>Unity勉強会2023</li>
        <li>DTM練習会2023</li>
        <li>簡潔データ構造をつくろう</li>
        <li>分散システム勉強会</li>
        <li>プログラミング入門2023</li>
      </ul>     
    </div>
    <img src="./kmc.png" alt="KMC Logo">
    <div class="buttons">
      <button id="button1" type="button">これはボタンです</button>
      <button id="button2" type="button">これもボタンです</button>
      <button id="button3" type="button">これも実はボタンです</button>
    </div>
  </body>
</html>
```

## 指定方法

### [要素名による指定](https://developer.mozilla.org/ja/docs/Web/CSS/Type_selectors)

要素名を直接記述します。

```css
body {
  background-color: #333333;
  color: white;
}

a {
  color: #cccccc;
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

### [クラスによる指定](https://developer.mozilla.org/ja/docs/Web/CSS/Class_selectors)

クラス名の前に`.`を付けて指定します。

```css
.projects {
  border-radius: 8px;
  box-shadow: 0 0 4px #77777777;
  display: inline-block;
  padding: 8px;
  margin: 10px;
}
```

### [idによる指定](https://developer.mozilla.org/ja/docs/Web/CSS/ID_selectors)

id名の前に`#`を付けて指定します。

```css
#button1 {
  color: white;
  background-color: #36b9ec;
  box-shadow: 3px 3px 5px #77777777;
  border-color: #00000000;
  border-radius: 8px;
  padding: 10px;
  margin: 15px;
}
```

### [属性による指定](https://developer.mozilla.org/ja/docs/Web/CSS/Attribute_selectors)

`[{属性名}={属性値}]`の形式で指定します。属性値が存在しない場合は、`[{属性名}]`の形式で指定します。


```css
a [href="https://kmc.gr.jp/"] {
  color: green;
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
  color: #eeeeee;
}
```

### 背景色

要素の背景色を指定するには、[`background-color`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/background-color)を使用します。

```css
body {
  background-color: gray;
}
```

### 背景画像

### フォント
フォントの指定には、[`font-family`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/font-family)を使用します。

```css
p {
  font-family: Gill Sans Extrabold, sans-serif;
}
```

フォントサイズの指定には、[`font-size`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/font-size)を使用します。

```css
.projects {
  font-size: 12px;
}
```

```css
.projects {
  font-size: 1.2em;
}
```

```css
.projects {
  font-size: smaller;
}
```

### 太字・斜体

太字の指定には、[`font-weight`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/font-weight)を使用します。

```css
h1 {
  font-weight: bold;
}
```

```css
h1 {
  font-weight: lighter;
}
```

斜体の指定には、[`font-style`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/font-style)を使用します。

```css
h1 {
  font-style: italic;
}
```

### テキスト修飾

テキスト装飾の指定には、[`text-decoration`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/text-decoration)を使用します。

```css
.message-important {
  text-decoration: red wavy underline;
}
```

### 文字間隔

文字間隔の指定には、[`letter-spacing`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/letter-spacing)を使用します。

```css
.projects {
  letter-spacing: .2rem;
}
```

```css
.projects {
  letter-spacing: -1px;
}
```

### 行の高さ

行の高さの指定には、[`line-height`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/line-height)を使用します。

`line-height`プロパティには、単位のない値を指定するのが好ましいとされています。

```css
.projects {
  line-height: 2;
}
```

### 枠線

枠線の指定には、[`border`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/border)を使用します。

```css
.projects {
  border: 1px solid orange;
}
```

```css
.projects {
  border: thick double #32a1ce;
}
```

### 角丸

角丸の指定には、[`border-radius`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/border-radius)を使用します。

```css
button {
    border-radius: 32px;
}
```

### 透明度

要素全体の指定には、[`opacity`プロパティ](https://developer.mozilla.org/ja/docs/Web/CSS/opacity)を使用します。

このプロパティは子要素にも継承されます。

背景色のみを透過したり、テキスト色のみを透過したりする場合は、背景色やテキスト色を透明度付きの色で指定してください。

```css
img {
  opacity: 0.5;
}
```

### 幅・高さ

```css
img {
  height: 250px;
  width: 500px;
}
```

### paddingとmargin

余白を指定するプロパティに、`padding`と`margin`があります

`padding`は、枠より内側の余白を、`margin`は枠より外側の余白を指定します
以下のcssを使うと分かりやすいでしょう。

```css
.buttons {
  border: 2px solid orange;
}

#button1 {
    border: 2px solid blue;
    margin: 0;
    padding: 0;
}

#button2 {
    border: 2px solid blue;
    margin: 50px;
    padding: 0px;
}

#button3 {
    border: 2px solid blue;
    margin: 0px;
    padding: 50px;
}
```

CSSについてはこれくらいにしておきます。
基本的な事項さえ理解していれば後は、「やりたいこと+CSS」で検索すれば大抵のことはできるでしょう。
より詳しく学びたい人は [MDNのCSSの章](https://developer.mozilla.org/ja/docs/Learn/CSS) を見てみましょう。

## JavaScript

JavaScriptは、ページに大して動的な変化を与えるときに使われるスクリプト言語です。

まずは、`index.html`と同じディレクトリにある`script.js`を次のように変更します。

```js
document.addEventListener('DOMContentLoaded', () => {
  const buttons = document.querySelectorAll('button');

  for (const button of buttons) {
    button.addEventListener('click', createParagraph);
  }

  function createParagraph() {
    const p = document.createElement('p');
    p.textContent = 'ボタンが押されました!';
    document.body.appendChild(p);
  }
});
```

さて、ブラウザを見てください。特に見た目では何も変わっていませんね。

では、三つあるボタン、どれでもいいので押してみましょう。どうなりましたか？

「ボタンが押されました!」という文字列が下の方に表示されたのではないでしょうか。

このように、JavaScriptを使うと、「ボタンが押されたとき」などの動的なイベントによって、新しく要素を追加/削除したり、編集したりできるのです。

動作を簡単に追ってみます。

まず、`script.js`自体は、`index.html`の、`html.head.script`の部分で読み込まれています。ここで、`defer`属性をつけることで、JavaScriptの読み込みを待たずにHTMLを読み込み、DOMを作ります。HTMLは上から順番に読み込まれていくので、こうしておかないとJavaScriptが読み込まれた後の要素にアクセスできなくなってしまいます。

さて、`script.js`が無事に読み込まれたので中身の処理を見ていきます。
まず、

```js
document.addEventListener('DOMContentLoaded', () => {
  ...
});
```

とありますね。`document`はブラウザで表示されているウェブページを表しています。Webページのコンテンツは、「DOM（Document Object Model）」として表現されます。

そして、`addEventListener`はターゲットで特定のイベントが起こった時に呼び出される関数を設定します。今回は、`DOMContentLoaded`、つまりページが読み込まれた時に、第二引数のコールバック関数が実行されます。

コールバック関数の中身は

```js
const buttons = document.querySelectorAll('button');

for (const button of buttons) {
  button.addEventListener('click', createParagraph);
}

function createParagraph() {
  const p = document.createElement('p');
  p.textContent = 'ボタンが押されました!';
  document.body.appendChild(p);
}
```

のようになっています。

まず、
```js
const buttons = document.querySelectorAll('button');
```

の部分では、`querySelectorAll`を使って、条件に合う要素一覧を取得しています。条件の部分はCSSでのセレクタと同じように指定してください。

そしてその一覧を`buttons`という名前の変数に保存します。

次に

```js
for (const button of buttons) {
  button.addEventListener('click', createParagraph);
}
```

`for`を使って、`buttons`の中身一つずつに処理を実行します。
その処理内容は、`addEventListener`を使い、ボタンに対して`click`イベントが起こった時に`createParagraph`関数を実行してね、と設定することです。

`createParagraph`関数はその次で定義されています。

```js
function createParagraph() {
  const p = document.createElement('p');
  p.textContent = 'ボタンが押されました!';
  document.body.appendChild(p);
}
```

まず、`document.createElement('p')`で、`<p>`要素を作り、`p`という変数に入れます。
そして次に、`p`の`textContent`というプロパティに「ボタンが押されました!」という文字列を設定します。つまりこれは`<p>ボタンが押されました!</p>`と同じです。

最後に、`document`の`<body>`に対して、`p`要素を追加します。

よって、みなさんに見てもらったように、ボタンを押すと「ボタンが押されました!」がどんどん追加されるような挙動になったのです。


さて、簡単にJavaScriptとその動きが分かったところで、[MDNの入門講座の題材](https://developer.mozilla.org/ja/docs/Learn/JavaScript/First_steps/A_first_splash)にチャレンジしてみましょう！

今回は数あてゲームを作ります。ランダムに生成した1~100までの数字を10回以内に当てていくゲームです。

さて、まずはHTMLを用意します

`index.html`を次のように書き換えましょう。

```html
<!DOCTYPE html>
<html lang="ja-JP">
  <head>
    <meta charset="utf-8" />
    <link rel="stylesheet" href="style.css" />
    <script src="script.js" defer></script>
    <title>section 03 | 2023-web</title>
  </head>
  <body>
    <h1>数字当てゲーム</h1>
    <p>1 から 100 までの数字を当ててみて！10 回以内に当てられるでしょうか。選んだ数字が大きいか小さいかを表示します。</p>
    <div class="form">
      <label for="guessField">予想を入力してください: </label>
      <input type="text" id="guessField" class="guessField" />
      <input type="submit" value="予想を送信" class="guessSubmit" />
    </div>
    <div class="resultParas">
      <p class="guesses"></p>
      <p class="lastResult"></p>
      <p class="lowOrHi"></p>
    </div>
  </body>
</html>
```

タイトルの`h1`、ゲームの説明用の`p`、答えを投稿するフォームとそのテキスト、入力ボックス、送信ボタンを追加しました。

その下の`resultParas`は結果の表示に使います。今のところその中身は空なのでブラウザでは真っ白です。

さて、次に`script.js`を書き換えます。

まずは今までの物を消して、以下の通りにします

```js
document.addEventListener("DOMContentLoaded", () => {
    let randomNumber = Math.floor(Math.random() * 100) + 1;

    const guesses = document.querySelector('.guesses');
    const lastResult = document.querySelector('.lastResult');
    const lowOrHi = document.querySelector('.lowOrHi');

    const guessSubmit = document.querySelector('.guessSubmit');
    const guessField = document.querySelector('.guessField');

    let guessCount = 1;
    let resetButton;

    guessField.focus();
});
```

色々書きましたね。`addEventListener`はさっきと同じなので置いておいて、そのコールバック関数の中身を見ていきます。

まず最初に答えとなる乱数を設定します。`Math.random()`は0以上1未満の乱数を生成するので、百倍して、整数部分を取り出すことで0～99の乱数を取り出し、+1して1～100までの乱数が取り出せますね。結果は`randomNumber`に格納しておきます。

次に`querySelector`で
`<p class="guesses"></p>` 
`<p class="lastResult"></p>` 
`<p class="lowOrHi"></p>`
の三つを探し出して、それぞれ変数に代入します。この要素の子要素を書き換えることでメッセージなどを表示させていきます。

同じようにして、入力ボックスの`guessField`、送信ボタンの`guessSubmit`も変数に代入します。

そして、`guessCount`という、予想回数を入れておく変数を作り、1を入れておきます。

`resetButton`の変数も最初に作っておきます。中身はまだ空です。

さて、`guessField.focus()`を入れてあげることで、ページが読み込まれたとき、自動的にカーソルが`guessField`、つまり入力欄に飛ぶようにしておきます。こうしておくと最初に入力ボックスをマウスでクリックする必要はなく、すぐに数字を入力できます。このような細かい親切設計は重要です。

さて、次に`checkGuess()`関数を作ります。これは、`guessSubmit.addEventListener('click', checkGuess);`として、送信ボタンを押したときに実行される関数です。

`guessField.focus();`の下に以下を追加します。

```js
function checkGuess() {
  let userGuess = Number(guessField.value);
  if (guessCount === 1) {
    guesses.textContent = '前回の予想: ';
  }
  guesses.textContent += userGuess + ' ';

  if (userGuess === randomNumber) {
    lastResult.textContent = 'おめでとう! 正解です!';
    lastResult.style.backgroundColor = 'green';
    lowOrHi.textContent = '';
    setGameOver();
  } else if (guessCount === 10) {
    lastResult.textContent = '!!!ゲームオーバー!!!';
    setGameOver();
  } else {
    lastResult.textContent = '間違いです!';
    lastResult.style.backgroundColor = 'red';
    if(userGuess < randomNumber) {
      lowOrHi.textContent='今の予想は小さすぎです!' ;
    } else if(userGuess > randomNumber) {
      lowOrHi.textContent = '今の予想は大きすぎです!';
    }
  }

  guessCount++;
  guessField.value = '';
  guessField.focus();
}

guessSubmit.addEventListener('click', checkGuess);
```
長いですが一つずつ見ていきましょう。

`checkGuess()`の中ではまず、`userGuess`を定義し、その中身は`Number(guessField.value)`となっています。つまり、「`guessField`=入力ボックス」の中身のテキストを数字に変換して代入しているのです。

つぎに
```js
if (guessCount === 1) {
  guesses.textContent = '前回の予想: ';
}
```
では、`guessCount === 1`、つまり、初回の入力の時にだけ、`guesses`=`<p class="guesses">`に対して、「前回の予想: 」というテキストを追加しています。

次に、`guesses.textContent += userGuess + ' ';`
の部分で、もともとの`guesses.textContent`の中身に`userGuess`つまり、ユーザーから受け付けた数字を追記します。こうすると前回予想した数字が羅列されるのでわかりやすいですね。

次は、クソ長条件分岐ですね。

```js
if (userGuess === randomNumber) {
  lastResult.textContent = 'おめでとう! 正解です!';
  lastResult.style.backgroundColor = 'green';
  lowOrHi.textContent = '';
  setGameOver();
} else if (guessCount === 10) {
  lastResult.textContent = '!!!ゲームオーバー!!!';
  setGameOver();
} else {
  lastResult.textContent = '間違いです!';
  lastResult.style.backgroundColor = 'red';
  if(userGuess < randomNumber) {
    lowOrHi.textContent='今の予想は小さすぎです!';
  } else if(userGuess > randomNumber) {
    lowOrHi.textContent = '今の予想は大きすぎです!';
  }
}
```

まず、`(userGuess === randomNumber)`の部分で、入力された数字と答えの数字が一致しているかどうかをみます。ここで等しければ、 `lastResult.textContent`、つまり`<p class="lastResult"></p>` のテキスト部分を、「おめでとう! 正解です!」に変更します。

そして、`lastResult.style.backgroundColor = 'green';`の部分で背景の色を緑色にします。
最後に、`lowOrHi.textContent = '';`によって、結果表示部分のテキストを空にしてあげます。

`setGameOver()`は、ゲーム終了後のふるまいを定義した関数です。今のところまだ存在しないですが放置します。

さて、正解ではなかった時、`(guessCount === 10)`を行い、試行回数が10回になったかどうかを判定します。今回は、予想は10回までという仕様だったので、`guessCount`が10になった時ゲームオーバーにします。

中身は、`lastResult.textContent = '!!!ゲームオーバー!!!';`によってゲームオーバーだよ～と伝え、`setGameOver()`を実行して、ゲームを終了させます。

最後にどちらに当てはまらなかった場合、つまり不正解だった場合、`lastResult.style.backgroundColor = 'red';`で背景を赤色にします。

そして間違いの中にも大きすぎと小さすぎがありますね。`if(userGuess < randomNumber)`で判定します。

入力が大きすぎたときは`lowOrHi.textContent='今の予想は小さすぎです!'`によって、結果を表示してあげます。

逆に小さかったときは`lowOrHi.textContent = '今の予想は大きすぎです!';`とします。

条件分岐を抜けたら最後に

```js
guessCount++;
guessField.value = '';
guessField.focus();
```

を追加します。

`guessCount++`は`guessCount = guessCount + 1`と同値です。送信ボタンが押されるたびに、実行回数のカウントを進めていくのですね。

そして、次の試行の際に入力ボックスに前回の数字が残っていると邪魔ですね。なので`guessField.value=''`で、中身を空にします。

そして最後に`guessField.focus()`を実行して入力ボックスにフォーカスを与えてあげます。

ここまでが`checkGuess()`関数でした。

最後に、この関数を`addEventListener`を使って、提出ボタンに付けてあげます！
`guessSubmit.addEventListener('click', checkGuess);`の部分ですね。


さぁ！これで正誤判定まで完成しました！一度遊んでみましょう！！`setGameOver()`がまだ定義されていないのでエラーが出ますが無視しましょう！

さて、今の状態では一度しか遊べませんね。繰り返し遊べるように変更しましょう。そのために`setGameOver()`を作ります。

以下コードを`guessSubmit.addEventListener('click', checkGuess);`の下に追加しましょう。

```js
function setGameOver() {
  guessField.disabled = true;
  guessSubmit.disabled = true;
  resetButton = document.createElement('button');
  resetButton.textContent = '新しいゲームを始める';
  document.body.appendChild(resetButton);
  resetButton.addEventListener('click', resetGame);
}
```

中身を見ていきます。

まずは、入力ボックスと提出ボックスを無効化します！
ゲーム終了後にも予想できたら意味がないですね。

```js
guessField.disabled = true;
guessSubmit.disabled = true;
```

とすれば無効化されます。

次にゲームのリセットボタンを追加します。
resetButton自体の定義は上の方でしました。

```js
resetButton = document.createElement('button');
```

で新しいボタン要素を作成します。

```js
resetButton.textContent = '新しいゲームを始める';
```

そしてボタンのテキストを「新しいゲームを始める」にします。

作ったボタンを

```js
document.body.appendChild(resetButton);
```

で`body`に追加してあげます。

最後に

```js
resetButton.addEventListener('click', resetGame);
```

で、作ったボタンに対して、`addEventListener`でクリック時に実行するコールバック関数を指定してあげます。

ここまでが`setGameOver()`関数です。

さて、リセットボタンを押したときに実行される`resetGame()`も作る必要が出てきました。作りましょう！

`function setGameOver() {}`
の下に

```js
function resetGame() {
  guessCount = 1;

  const resetParas = document.querySelectorAll('.resultParas p');
  for (let i = 0 ; i < resetParas.length ; i++) {
    resetParas[i].textContent = '';
  }

  resetButton.parentNode.removeChild(resetButton);

  guessField.disabled = false;
  guessSubmit.disabled = false;
  guessField.value = '';
  guessField.focus();

  lastResult.style.backgroundColor = 'white';

  randomNumber = Math.floor(Math.random() * 100) + 1;
}
```

を追記します。

まず、`guessCount = 1;`で試行回数を1にリセットします。
次に、`const resetParas = document.querySelectorAll('.resultParas p');`で、`<div class="resultParas">`の中の子要素`<p>`を検索して、その一覧を`resetParas`に入れてあげます。

言い忘れていますが、`querySelectorAll`のセレクタ部分は、スペース区切りで複数設定できます。今回は`class=resultParas`かつ、`<p>`要素というものにヒットします。`class`については親要素に設定されているので、その子要素にも適用されます。

```js
  for (let i = 0 ; i < resetParas.length ; i++) {
    resetParas[i].textContent = '';
  }
```

の部分では、取得してきた`<p>`要素たちに対して、全てのテキストを空にしています。前回の結果のテキストなどが残っていてはいけませんからね。

```js
resetButton.parentNode.removeChild(resetButton);
```

の部分は、resetButtonを消すためのコードです。

`resetButton.parentNode`で、resetButtonの親要素、つまり`<body>`を指定します。そしてそこから`removeChild(resetButton)`で、resetButtonを削除しています。


```js
guessField.disabled = false;
guessSubmit.disabled = false;
```

では先ほど無効化した入力ボックスと送信ボタンを再度有効化します。`disabled`が`false`なので`enabled`ですね。

あともう少しです。

```js
guessField.value = '';
guessField.focus();
```

で、入力ボックスの中身を空にします。
そして、最後にまたまた入力ボックスにフォーカスさせます。

あ、背景の色を変更したのを忘れていましたね。元の色に戻してあげましょう。

```js
lastResult.style.backgroundColor = 'white';
```
これで白色に戻りました。

いよいよ最後です！乱数をもう一度生成します！

一番最初とほとんど同じですが、`let`を付けずに、既存の`randomNumber`を上書きするようにします。

```js
randomNumber = Math.floor(Math.random() * 100) + 1;
```

これで完成です！！！！
何回でも無限に遊べますね！

完成した`script.js`全体を以下にのせておきます！

```js
document.addEventListener("DOMContentLoaded", () => {
    let randomNumber = Math.floor(Math.random() * 100) + 1;

    const guesses = document.querySelector('.guesses');
    const lastResult = document.querySelector('.lastResult');
    const lowOrHi = document.querySelector('.lowOrHi');

    const guessSubmit = document.querySelector('.guessSubmit');
    const guessField = document.querySelector('.guessField');

    let guessCount = 1;
    let resetButton;

    guessField.focus();

    function checkGuess() {
        let userGuess = Number(guessField.value);
        if (guessCount === 1) {
          guesses.textContent = '前回の予想: ';
        }
        guesses.textContent += userGuess + ' ';
      
        if (userGuess === randomNumber) {
          lastResult.textContent = 'おめでとう! 正解です!';
          lastResult.style.backgroundColor = 'green';
          lowOrHi.textContent = '';
          setGameOver();
        } else if (guessCount === 10) {
          lastResult.textContent = '!!!ゲームオーバー!!!';
          setGameOver();
        } else {
          lastResult.textContent = '間違いです!';
          lastResult.style.backgroundColor = 'red';
          if(userGuess < randomNumber) {
            lowOrHi.textContent='今の予想は小さすぎです!' ;
          } else if(userGuess > randomNumber) {
            lowOrHi.textContent = '今の予想は大きすぎです!';
          }
        }
      
        guessCount++;
        guessField.value = '';
        guessField.focus();
      }

      guessSubmit.addEventListener('click', checkGuess);

      function setGameOver() {
        guessField.disabled = true;
        guessSubmit.disabled = true;
        resetButton = document.createElement('button');
        resetButton.textContent = '新しいゲームを始める';
        document.body.appendChild(resetButton);
        resetButton.addEventListener('click', resetGame);
      }

      function resetGame() {
        guessCount = 1;
      
        const resetParas = document.querySelectorAll('.resultParas p');
        for (let i = 0 ; i < resetParas.length ; i++) {
          resetParas[i].textContent = '';
        }
      
        resetButton.parentNode.removeChild(resetButton);
      
        guessField.disabled = false;
        guessSubmit.disabled = false;
        guessField.value = '';
        guessField.focus();
      
        lastResult.style.backgroundColor = 'white';
      
        randomNumber = Math.floor(Math.random() * 100) + 1;
      }
});
```

## 後片付け

ターミナルで`Ctrl+C`、`Y`を入力してサーバーを終了させます。
