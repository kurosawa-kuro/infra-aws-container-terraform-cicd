# Express練習用のAWS設定

## VPC設定

### 基本情報

- **リージョン**: 東京 (ap-northeast-1)
- **リソース**: VPCのみ
- **名前タグ**: training-vpc
- **IPv4 CIDRブロック**: 10.0.0.0/16

### サブネット

- **training-public-subnet-01**
  - **リージョン**: ap-northeast-1
  - **IPv4 CIDR**: 10.0.11.0/24

- **training-private-subnet-01**
  - **リージョン**: ap-northeast-1
  - **IPv4 CIDR**: 10.0.21.0/24

- **training-public-subnet-02**
  - **リージョン**: ap-northeast-2
  - **IPv4 CIDR**: 10.0.12.0/24

- **training-private-subnet-02**
  - **リージョン**: ap-northeast-2
  - **IPv4 CIDR**: 10.0.22.0/24

### インターネットゲートウェイ

- **名前タグ**: training-igw
- **VPCにアタッチ**: training-vpc

### ルートテーブル

- **名前タグ**: training-rt
- **VPC**: training-vpc
- **ルートの追加**: 
  - **送信先**: 0.0.0.0/0
  - **ターゲット**: インターネットゲートウェイ(training-IGW)
- **サブネットの関連付け**: 
  - **サブネット**: training-Public-Subnet-01
  - **ルートテーブル**: training-rt

## EC2設定

- **名前タグ**: training-ec2
- **OSイメージ**: Amazon Linux
- **ログイン用キーペア**: training-key
- **ネットワーク設定**:
  - **VPC**: training-vpc
  - **サブネット**: training-public-subnet-01
  - **パブリック IP の自動割り当て**: 有効化
  - **セキュリティグループ**: training-sg
    - **ルール**:
      - **種類**: カスタム TCP
      - **ポート範囲**: 8080
      - **ソースタイプ**: カスタム
      - **ソースIP範囲**: 0.0.0.0/0

## インスタンスに接続
<!-- ```bash
ssh -i "training-Key.pem" ec2-user@10.0.4.205
``` -->

## ソフトウェア設定

### Node.jsのインストール
<!-- ```bash
curl -sL https://rpm.nodesource.com/setup_16.x | sudo bash -
sudo yum install -y nodejs
``` -->

### Expressアプリのセットアップ

#### アプリディレクトリの初期化

<!-- ```bash
mkdir app
cd app
npm init -y
npm install express
touch index.js
``` -->

#### サーバーファイルの作成

<!-- ```bash
const express = require("express");

const app = express();

app.get("/", (req, res) => {
  res.send("Hello World");
});

app.listen(8080, () => {
  console.log("listening");
});
``` -->

## 終了方法

- ec2のインスタンスを終了する
- サブネットの削除
- ルートテーブルの削除
- インターネットゲートウェイのデタッチ
- インターネットゲートウェイの削除
- VPCの削除
