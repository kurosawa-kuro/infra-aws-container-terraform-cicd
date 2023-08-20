# EC2-Expressの設定とアプリケーションセットアップ

## VPC

### VPC の設定

- 作成するリソース
  - VPCのみ

- 名前タグ
  - training-vpc

- IPv4 CIDR
  - 10.0.0.0/24

## EC2

### OSイメージ

- Amazon Linux

## ログイン用キーペア

- training-pair

## ネットワーク設定

- セキュリティグループ: `ec2_express-sg`
  - ルール:
        - 種類: カスタム TCP
        - ポート範囲: 5000
        - ソースタイプ: カスタム
        - ソースIP範囲: 0.0.0.0/0

---

### Node.jsのインストール

```bash
curl -sL https://rpm.nodesource.com/setup_16.x | sudo bash -
sudo yum install -y nodejs
```

### Expressアプリのセットアップ

#### アプリディレクトリの初期化

```bash
mkdir app
cd app
npm init -y
npm install express
touch index.js
```

#### サーバーファイルの作成

```javascript
const express = require("express");

const app = express();

app.get("/", (req, res) => {
  res.send("Hello World");
});

app.listen(5000, () => {
  console.log("listening");
});
```
