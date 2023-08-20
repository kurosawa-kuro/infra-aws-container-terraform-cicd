# Express練習用のAWS設定



## EC2設定

- **名前タグ**: training-ec2
- **OSイメージ**: Amazon Linux
- **ログイン用キーペア**: training-key
- **ネットワーク設定**:
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
sudo yum update -y

sudo yum install git -y

sudo amazon-linux-extras install docker -y
sudo service docker start
sudo usermod -a -G docker ec2-user
``` -->

### Expressアプリのセットアップ

#### アプリディレクトリの初期化

<!-- ```bash
git clone 
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
