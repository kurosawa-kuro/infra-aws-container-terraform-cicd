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
ssh -i "training-key.pem" ec2-user@ec2-35-77-106-245.ap-northeast-1.compute.amazonaws.com
``` -->

## ソフトウェア設定

### dockerのインストール
<!-- ```bash
sudo yum update -y

sudo yum install git -y

sudo yum install docker -y
sudo service docker start
sudo usermod -a -G docker ec2-user

exit

``` -->

<!-- ```bash
sudo yum install -y libxcrypt-compat

sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
``` -->

### Expressアプリのセットアップ

#### アプリディレクトリの初期化

<!-- ```bash
git clone https://github.com/kurosawa-kuro/infra-aws-container-terraform-cicd.git
``` -->

#### docker起動

<!-- ```bash
cd infra-aws-container-terraform-cicd/ec2-nodejs-app-compose/
docker-compose up
``` -->

## 終了方法

- ec2のインスタンスを終了する
- サブネットの削除
- ルートテーブルの削除
- インターネットゲートウェイのデタッチ
- インターネットゲートウェイの削除
- VPCの削除
