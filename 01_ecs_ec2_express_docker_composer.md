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
ssh -i "training-key.pem" ec2-user@ec2-13-230-221-241.ap-northeast-1.compute.amazonaws.com
``` -->

## ソフトウェア設定

### dockerのインストール
<!-- ```bash
sudo yum update -y

sudo yum install git -y

sudo yum install docker -y
sudo service docker start
sudo usermod -a -G docker ec2-user

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

exit

``` -->

<!-- ```bash
sudo yum install -y libxcrypt-compat

sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
``` -->

### Fargateのセットアップ

#### コンテナの登録

<!-- ```bash
git clone https://github.com/kurosawa-kuro/infra-aws-container-terraform-cicd.git
``` -->

#### Fargateの設定

<!-- ```bash
cd infra-aws-container-terraform-cicd/ec2-nodejs-app-compose/
docker-compose up
``` -->

```bash
training-cluster
training-task
8080
training-container
training-service
training-sg
```

## 終了方法

- タスク停止
- タスク登録削除
- タスク削除
- サービス削除
- クラスター削除
