# Webサービス勉強会2023 第二回

(2023/05/21)

HTMLとCSSについて、一緒に手を動かしながら簡単におさらいしましょう！

## 準備

環境構築が終わっていない人は[第一回資料](../section01/README.md)を基に構築してください。

1. Section02の追加を手元に取得します

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

3. section02に移動します

```bash
cd ~/section02
```

4. サーバーを起動します

```bash
npm run dev
```

5. ブラウザからアクセスします

自動的に開くと思います

開かなければ <http://localhost:8080> にアクセス

Hello World!と表示されていればOKです！

いったんCtrl+Cで止めます

### HTMLの編集

1.  VSCodeの起動

~/2023-web/section02をターミナルで開いている状態で

```bash
code .
```
とするとVSCodeで開きます

2. index.htmlを探す

~/2023-web/section02/index.htmlです

![](../resources/2023-05-21_13h15_42.png)

3. 中身を見る

```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
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

今日の講習会中はちけっぱにします

5. index.htmlを編集してみる

Hello World! の部分を自分の名前に変えて保存しましょう

保存すると、ブラウザ側も自動的に変更が反映されるはずです、便利～

## HTML講座

この章では実際に↑のindex.htmlを書き換えて試してみてください

### HTML要素

HTMLはタグで囲むことでいろいろな要素を表現します。

例えば

```html
<P> 段落 </p>
```

で囲むと段落を表現します。

要素の中に要素をかくのもOKです

```html
<div>
	<P>段落</p>
</div>
```

ここで、`<foo>`や`</foo>`をタグと呼びます。
<foo>の形をしたものを開始タグ、</foo>の形をしたものを終了タグと呼びます。
開始タグと終了タグは基本的にセットで使います。

ただし、たとえば`<img>`などは

```html
<img src="https://www.kmc.gr.jp/assets/logo-dd0898d76a871e83d6bb7df9fd2a66c538fa422f4ab33698ba15ac051178cbe498ce88428bddb89f10e8a6791901b4a1e1af0589530deaf858f91cc8bf8fee25.png">
```

というように、開始タグしかありません。
このようなものは空要素と呼ばれます。

それぞれのタグに対しては、`属性`を付けることができます。

ただしこれは必ず付けなければならないものではありません。

たとえば、`id`は、要素を一意にラベル付けします。`id`は重複があってはいけません。そのため、`id`さえしていすればどの要素を指しているか判別できます。

`class`は、要素をスタイル情報の対象とするために使用されます。`class`は複数の要素に同じクラス名をつけてもよいです。
また、一つの要素に複数のクラスを付けてもOKです。

例えば

```html
<p class="red">このテキストにスタイルが適用されます</p>
```

とし、CSSに

```css
p.red { color: red; }
```

と書くと、`<p>`の`class="red"`に対し、全て文字色は赤になります。

`id`と`class`はどの要素でも頻繁に使うので覚えておきましょう。

その他、特定のTagに特定の属性があります。

例えば`<a>`を使います。

`<a>`は、リンクを作ります

```html
<a href="https://kmc.gr.jp" title="KMC公式" target="_blank"> KMC公式サイト </a>
```

などと使います。
ここでは
- `href`
- `title`
- `target`

の属性を指定しました。

`href`はリンクURL、`title`はマウスカーソルを乗せたときに出るテキスト、`target`はリンクの開く先を指定します（新しいタブで開くかどうかなど）

このように属性は複数つけることができます。

普通、`属性名="属性値"`の形で書きますが、属性値の部分が省略されていることがあります。

これは、論理属性といい、一般的に属性名と同じ属性値だけを取ることができます。

例えば、`<input>`（入力欄を作る）を使うとき、

```html
<input type="text" disabled>
```

と

```html
<input type="text" disabled="disabled">
```

は、同じです。

### 要素の紹介

要素にはブロック要素とインライン要素があります

ブロック要素は`<p>`や`<div>`などです
ウェブページの中でのブロックを表します

インライン要素はブロックレベル要素の中に書かれるもので、`<a>`や`<strong>`などです。

要素をいろいろ紹介していきます

### [h1, h2, h3, h4, h5, h6](https://developer.mozilla.org/ja/docs/Web/HTML/Element/Heading_Elements)

見出しを表示するために使用します。h1は最上位、h2, h3, ...の順に見出しレベルが下がります。

見出しレベルは飛ばしてはいけません。また、h1の複数回の使用は避けるのが無難です。


##### 見出し要素の使用に関する注意点

一般的なウェブブラウザでは、見出し要素は大きなフォントサイズ・太字で描画されます。しかし、HTMLは文章の構造を表すためのものであり、**スタイルの調整にHTMLを用いてはいけません。** スタイルは全てCSSを用いて調整します。**文字サイズを大きくする目的で見出し要素を使用してはいけません。**

詳しくは、CSSでお話しします

```html
<h1>KMC</h1>

<!-- 省略 -->

<h2>KMCの活動</h2>

<!-- 省略 -->

<h2>今後の予定</h2>

<!-- 省略 -->

```

#### [p](https://developer.mozilla.org/ja/docs/Web/HTML/Element/p)

テキストを表示する際に使用します。

```html
<p>カラスは黒い鳥</p>
```

#### [br](https://developer.mozilla.org/ja/docs/Web/HTML/Element/br)

テキストを改行する際に使用します。終了タグを記述しない点が特徴です。

```html
<p>カラスは黒い鳥<br>黒くない鳥はカラスではない</p>
```

##### 改行要素の使用に関する注意点

要素間にスペースを開けるために、brを使用してはいけません。スペースを調整するためには、CSSを用います。

これについても、CSSの説明時に詳しく扱います。

#### [a](https://developer.mozilla.org/ja/docs/Web/HTML/Element/a)

ハイパーリンクの作成に使用します。リンク先を指定するには、`href`属性を使用します。また、リンク先を新しいタブで開くようにする場合は、`target`属性を用いて`target="_blank"`と指定します。

```html
<a href="https://example.com" target="_blank">テストリンク</a>
```

##### ページ内リンクの作成

ページ内リンクを貼る場合は、`href`属性の値に`#{飛ぶ先の要素のid名}`を指定します。

```html
<h1>予約サイト</h1>
<p>
  <a href="#register-form">予約はこちら</a>
</p>

<!-- 省略 -->

<h2 id="register-form">予約</h2>
<div>
  <p>お名前</p>
  <input type="text">
  <p>メール</p>
  <input type="email">
</div>
```

#### [img](https://developer.mozilla.org/ja/docs/Web/HTML/Element/img)

画像を表示するために使用します。表示する画像のパスを、`src`属性を用いて記述します。

`alt`属性は必須ではありませんが、特別な理由がない限り、必ず書くようにすべきです。
画像が表示できない環境や、スクリーンリーダーでALTのテキストが用いられます。

```html
<img src="./kmc.png" alt="KMC Logo">
```

#### [div](https://developer.mozilla.org/ja/docs/Web/HTML/Element/div)

divタグは、複数の要素をまとめるために使用します。

```html
<div>
  <p>お名前</p>
  <input type="text">
  <p>メール</p>
  <input type="email">
</div>
```

#### [span](https://developer.mozilla.org/ja/docs/Web/HTML/Element/span)

spanタグも、複数の要素をまとめるために使用します。

```html
<span><a href="https://example.com" target="_blank">ここ</a>をクリック</span>
```

#### コメントアウト

以下の形式でコメントアウトが可能です。

```html
<!-- ここはコメント -->
```

#### [em](https://developer.mozilla.org/ja/docs/Web/HTML/Element/em)

テキストを強調します。

```html
<em>英数字8文字以上</em>で入力してください。
```

#### [strong](https://developer.mozilla.org/ja/docs/Web/HTML/Element/strong)

重要、重大、または緊急性の高いテキストを表します。

```html
電源ボタンを<strong>3秒間長押し</strong>することで、強制的に終了します。
```

#### [ol](https://developer.mozilla.org/ja/docs/Web/HTML/Element/ol)

順序付きのリストを表します。

`ol`タグは、中に1つ以上の`li`要素を含めて使用します。

```html
<ol>
  <li>東京</li>
  <li>大阪</li>
  <li>神奈川</li>
</ol>
```

#### [ul](https://developer.mozilla.org/ja/docs/Web/HTML/Element/ul)

箇条書き (順序なしのリスト) を表します。

`ul`タグも、中に1つ以上の`li`要素を含めて使用します。

```html
<ul>
  <li>リンゴ</li>
  <li>ミカン</li>
  <li>スイカ</li>
</ul>
```

#### [li](https://developer.mozilla.org/ja/docs/Web/HTML/Element/li)

リストの項目を表します。

`li`タグは、上述の`ol`タグまたは`ul`タグの中に配置して使用します。

##### リスト作成時の注意点

`ol`タグと`ul`タグの中に含められるタグは、基本的に`li`要素のみです。

#### [button](https://developer.mozilla.org/ja/docs/Web/HTML/Element/button)

ボタンを表します。

```html
<button>Submit</button>
```

#### [input](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input)

データ入力用の様々なコントロールを作成します。

作成するコントロールの種類は`type`属性で指定します。

##### テキスト (1行) 入力用コントロール

```html
<input type="text" name="user-name" id="user-name">
```

##### メールアドレス入力用コントロール

```html
<input type="email" name="email-address" id="email-address">
```

##### パスワード入力用コントロール

```html
<input type="password" name="user-password" id="user-password">
```

##### 数字入力用コントロール

```html
<input type="number" name="age" id="age">
```

##### ボタン

```html
<input type="button" value="ボタン">
```

##### チェックボックス

```html
<input type="checkbox" name="has-read" id="has-read">
```

##### ラジオホタン

```html
<input type="radio" name="contact" id="contact-email">
```

##### 日付選択用コントロール

```html
<input type="date" name="birthday" id="birthday">
```

##### 時間入力用コントロール

```html
<input type="time" name="start-time" id="start-time">
```

##### ファイル選択用コントロール

```html
<input type="file" name="profile-icon" id="profile-icon">
```

##### スライダーコントロール

```html
<input type="range" name="volume" id="volume">
```

##### 色選択用コントロール

```html
<input type="color" name="text-color" id="text-color">
```

##### リセット用コントロール

```html
<input type="reset" value="リセット">
```

#### [label](https://developer.mozilla.org/ja/docs/Web/HTML/Element/label)

`label`要素は、`input`要素とともに用いられることが多く、主に`input`要素のヒット領域を広げる目的で使用されます。

`input`要素と`label`要素を関連付ける方法は、以下の2つがあります。

この方法を用いることで、テキスト部分をクリックすることで`input`要素の切り替えを行うことができます。

##### `label`要素で`input`要素を囲む

```html
<label>
  <input type="checkbox" name="is-kmc-member" id="is-kmc-member">
  KMC部員
</label>
```

##### `label`要素の`for`属性を使用する

```html
<input type="checkbox" name="is-kmc-member" id="is-kmc-member">
<label for="is-kmc-member">KMC部員</label>
```

#### [progress](https://developer.mozilla.org/ja/docs/Web/HTML/Element/progress)

タスクの進捗を表します。

```html
<progress max="100" value="70"></progress>
```

#### [select](https://developer.mozilla.org/ja/docs/Web/HTML/Element/select)

選択式メニューを作成します。

`option`要素を用いてメニューを作成します。

```html
<select>
  <option value="dog">犬</option>
  <option value="cat">猫</option>
  <option value="rabbit">うさぎ</option>
</select>
```

#### [option](https://developer.mozilla.org/ja/docs/Web/HTML/Element/option)

メニュー項目を作成します。

#### [textarea](https://developer.mozilla.org/ja/docs/Web/HTML/Element/textarea)

```html
<textarea name="answer" id="answer" cols="30" rows="10">KMC</textarea>
```

複数行入力可能なテキスト入力用コントロールを作成します。

#### [form](https://developer.mozilla.org/ja/docs/Web/HTML/Element/form)

フォーム (サーバーに情報を送るパーツ) を表します。(今後、`form`から送られたデータを実際に受け取って処理をする話も扱う予定です)

以下は、`form`要素と`input`要素の使用方法の例です。フィールドを必須項目にするには、`required`属性を使用します。また、入力値ヒントを表示するには、`placeholder`属性を使用します。

> [HTML 属性: required | MDN](https://developer.mozilla.org/ja/docs/Web/HTML/Attributes/required)

> [placeholder 属性 | MDN](https://developer.mozilla.org/ja/docs/orphaned/Learn/HTML/Forms/HTML5_updates#the_placeholder_attribute)

```html
<form action="">
  <div>
    <input type="checkbox" name="can-read-lang" id="can-read-en">
    <label for="can-read-en">英語</label>
    <input type="checkbox" name="can-read-lang" id="can-read-ja">
    <label for="can-read-ja">日本語</label>
    <input type="checkbox" name="can-read-lang" id="can-read-fr">
    <label for="can-read-fr">フランス語</label>
  </div>
  <div>
    <label for="text-color">色の選択</label>
    <input type="color" name="text-color" id="text-color">
  </div>
  <div>
    <label for="birthday">生年月日</label>
    <input type="date" name="birthday" id="birthday">
  </div>
  <div>
    <label for="start-time">開始時刻</label>
    <input type="time" name="start-time" id="start-time">
  </div>
  <div>
    <label for="user-name">氏名</label>
    <input type="text" name="user-name" id="user-name" placeholder="山田太郎">
  </div>
  <div>
    <label for="email-address">メールアドレス</label>
    <input type="email" name="email-address" id="email-address">
  </div>
  <div>
    <label for="age">年齢</label>
    <input type="number" name="age" id="age">
  </div>
  <div>
    <label for="profile-icon">プロフィールアイコン</label>
    <input type="file" name="profile-icon" id="profile-icon">
  </div>
  <div>
    <label for="user-password">パスワード</label>
    <input type="password" name="user-password" id="user-password">
  </div>
  <div>
    <input type="radio" name="contact" id="contact-email">
    <label for="contact-email">メール</label>
    <input type="radio" name="contact" id="contact-phone">
    <label for="contact-phone">電話</label>
  </div>
  <div>
    <input type="range" name="volume" id="volume">
  </div>
  <div>
    <progress></progress>
  </div>
  <div>
    <progress max="100" value="80"></progress>
  </div>
  <div>
    <label for="address">居住地区</label>
    <select name="address" id="address">
      <option value="address-1">北海道</option>
      <option value="address-2">東北</option>
      <option value="address-3">関東</option>
      <option value="address-4">中部</option>
      <option value="address-5">関西</option>
      <option value="address-6">中国</option>
      <option value="address-7">四国</option>
      <option value="address-7">九州・沖縄</option>
    </select>
  </div>
  <div>
    <label for="others">備考</label>
    <textarea name="others" id="others" cols="30" rows="10" placeholder="自由に記述してください。"></textarea>
  </div>
  <div>
    <input type="reset" value="リセット">
    <input type="button" value="送信">
  </div>
</form>
```

#### [dl](https://developer.mozilla.org/ja/docs/Web/HTML/Element/dl)

`dl`タグ、`dt`タグ、`dd`タグを用いて、項目の説明や定義を記述することができます。

`dl`タグの中に`dt`タグと`dd`タグを配置します。

#### [dt](https://developer.mozilla.org/ja/docs/Web/HTML/Element/dt)

`dt`タグは説明/定義の対象となる用語を表します。

#### [dd](https://developer.mozilla.org/ja/docs/Web/HTML/Element/dd)

`dd`タグは`dt`タグで指定した用語の説明/定義を表します。

```html
<dl>
  <dt>アメリカ</dt>
  <dd>アメリカ合衆国</dd>

  <dt>イギリス</dt>
  <dd>グレートブリテン及び北アイルランド連合王国</dd>

  <dt>日本</dt>
  <dd>日本国</dd>
</dl>
```

#### [table](https://developer.mozilla.org/ja/docs/Web/HTML/Element/table)

表 (テーブル) を作成します。

#### [th](https://developer.mozilla.org/ja/docs/Web/HTML/Element/th)

表のヘッダーを表します。

#### [tr](https://developer.mozilla.org/ja/docs/Web/HTML/Element/tr)

表の行を表します。

#### [td](https://developer.mozilla.org/ja/docs/Web/HTML/Element/td)

表のセルを定義します。

#### [thead](https://developer.mozilla.org/ja/docs/Web/HTML/Element/thead)

表の列見出しを表します。

#### [tbody](https://developer.mozilla.org/ja/docs/Web/HTML/Element/tbody)

表の本体部分を表します。

#### [tfoot](https://developer.mozilla.org/ja/docs/Web/HTML/Element/tfoot)

表の列フッターを表します。

```html
<table>
  <thead>
    <tr>
      <th>市町村</th>
      <th>人口 (万人)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>大阪市</th>
      <td>275</td>
    </tr>
    <tr>
      <th>横浜市</th>
      <td>372</td>
    </tr>
    <tr>
      <th>名古屋市</th>
      <td>233</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th>計</th>
      <td>880</td>
    </tr>
  </tfoot>
</table>
```
