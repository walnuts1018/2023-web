# Webサービス勉強会2023

## HTMLとCSSの基礎知識

HTMLとCSSについて、一緒に手を動かしながら簡単におさらいしましょう！

### 準備

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

開かなければ <http://localhost:3000> にアクセス

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

### HTML講座

