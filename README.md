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
```

---

## ■ Nginx（エンジンエックス）のインストールと起動確認

EC2 に接続後、Nginx をインストールし、起動と自動起動設定を行いました。

```bash
sudo dnf update -y
sudo dnf install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

Nginx（エンジンエックス）のインストールと起動確認
```bash
sudo systemctl status nginx
```

ブラウザで動作確認
```bash
http://＜パブリックIP＞
```

## ■ EBS（Elastic Block Store）の料金理解

EC2 インスタンスを停止しても、EBS（ディスク）はデータ保持のため課金されることを学びました。

- 東京リージョンの料金：**約 0.12 USD/GB/月**  
- 今回の構成（8GB）：**約100〜150円/月**  
- EC2 本体は停止中なら **0円**  
- EBS は環境を保持するための最低限のコスト

---

## ■ インスタンス停止とコスト最適化

学習終了後、インスタンスを停止しました。  
停止後の状態は以下の通りです。

- 状態：**停止中**  
- EC2 本体の料金：**0円**  
- EBS のみ少額課金が継続  
- 再起動すれば同じ環境で学習を再開可能  

停止はコスト最適化のための重要な操作であり、学習環境を維持しつつ費用を抑える方法として理解しました。

---

## ■ 学んだことまとめ

- EC2 の起動・停止の仕組み  
- SSH 接続と鍵認証の流れ  
- Nginx のインストールと動作確認（status / curl / ブラウザ確認）  
- EBS の料金体系（停止中でもディスクは課金）  
- AWS 環境を低コストで維持する方法  
