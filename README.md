# ECS FargatePHP + Nginx Sample

## 概要
PHP-FPM + Nginxの２コンテナ構成をAmazonECS on Fargateで動作確認するためのサンプルです。

## 構成
Browser
↓
PublicIP/ALB
↓
nginxContainer:80
↓ fastcgi_pass 127.0.0.1:9000
php-fpm container:9000

## 使用技術
- PHP8.5-FPM
- Nginx1.30.0
- Docker/Docker compose
- Amazon ECR
- Amazon ECS on Fargate

## 起動方法
docker/nginx/default.confのfastcgi_passをapp:9000に書き換えてから
起動
docker compose up -d
停止
docker compose down

## 発生した問題
Mac上でビルドしたDockerimageをECRにプッシュしたところFargate側で以下エラー発生。
image Manifest does not contain descriptor matching platform 'linux/amd64'

## 解決方法
linux/amd64を指定してビルド、プッシュを実施した。
docker buildx build \
  --platform linux/amd64 \
  --provenance=false \
  -f docker/nginx/Dockerfile \
  -t <私のAWSアカウントID>.dkr.ecr.ap-northeast-1.amazonaws.com/ecs-sample-nginx:latest \