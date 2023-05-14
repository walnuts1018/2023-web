# Webサービス勉強会2023

## 環境構築

### 🛠️ 必要なツール

- git
- vscode
- nodejs

### gitのインストール

#### <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/87/Windows_logo_-_2021.svg/768px-Windows_logo_-_2021.svg.png" height="30" width="30"> Windows の人

※ 5/13のみんげーに参加していただいた方は終わっているので読み飛ばしてください

1. <https://gitforwindows.org> にアクセス

2. Downloadボタンをクリック

![](../resources/2023-05-14_12h52_49.png)

3. ダウンロードしたインストーラーを開いてインストール

![](../resources/2023-05-14_12h58_44.png)

![](../resources/2023-05-14_12h58_58.png)

![](../resources/2023-05-14_12h59_07.png)

![](../resources/2023-05-14_12h59_17.png)

![](../resources/2023-05-14_12h59_26.png)

![](../resources/gitfinish.png)

4. PowerShellを開いて

```powershell
git --version
```

と入力

```powershell
git version 2.40.1.windows.1
```

みたいに表示されたら成功！

5. ユーザー名とメールアドレスを登録

```powershell
git config --global user.name "ユーザー名"
git config --global user.email "メールアドレス"
```

#### macの人

1. Launchpadから <img src="https://help.apple.com/assets/63D8162D4F5E9E311D0CFA28/63D816334F5E9E311D0CFA30/ja_JP/a1f94c9ca0de21571b88a8bf9aef36b8.png" alt="" height="30" width="30"> をクリックして、検索ボックスから「ターミナル」を検索

2. <img src="https://help.apple.com/assets/63D8162D4F5E9E311D0CFA28/63D816334F5E9E311D0CFA30/ja_JP/20f5edbfdfa0bd8ad4c4c6452e5b6761.png" alt="" height="30" width="30"> を起動

3. 

```zsh
git --version
```

を実行

```zsh
git version 2.30.2
```

みたいな表示が出てきたら最初から入っています。4.を飛ばして5. へ

4. 出てこなかった人はgitが入っていません

<https://brew.sh/index_ja> へアクセスして

![](../resources/2023-05-14_13h17_53.png)

のようにインストールコマンドをターミナルで実行

終わったら

```zsh
brew install git
```

を実行

再度

```zsh
git --version
```

を試してみてください。

