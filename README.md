# ec2-nginx-practice
AWS EC2 と Nginx の学習ログ
# AWS EC2 学習ログ（Nginx構築〜インスタンス停止まで）

## ■ 概要
Amazon EC2（Amazon Linux 2023）を使用して Web サーバ環境を構築し、  
Nginx のインストール・動作確認・インスタンス停止までを学習しました。  
本ログはその記録です。

---

## ■ EC2インスタンス作成
- AMI：Amazon Linux 2023
- インスタンスタイプ：t3.micro
- ストレージ：8GB（EBS）
- セキュリティグループ設定：
  - SSH（22）→ 自分のIPのみ許可
  - HTTP（80）→ 0.0.0.0/0（全世界からアクセス可能）

---

## ■ SSH接続
ローカル PC（Windows）から EC2 へ接続。

```bash
cd C:\Users\USER\Documents
ssh -i yuya-ec2-key.pem ec2-user@＜パブリックIP＞
