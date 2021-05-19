# Chat-app

Slackをイメージしたコミュニケーションチャットアプリです。   
ゲストログインからトークを作成して会話してみてください！   
二つの端末からログインすれば会話ができます！！   
   
   リンク：http://35.72.134.150:3000/

# 見本
<img width="800" alt="スクリーンショット 2021-04-12 21 59 17" src="https://user-images.githubusercontent.com/69971834/114398307-9cc0f800-9bda-11eb-9483-76db75c45e0e.png">


# 環境
ruby 2.6.5  
Ruby on rails 6.0.0  
mysql2 0.4.4  
unicorn 5.4.1  

# 使い方
気軽に体験頂けるように、「ゲストユーザー」機能をつけております。
画像右記よりログインください。
<img width="1437" alt="スクリーンショット 2021-04-12 22 11 34" src="https://user-images.githubusercontent.com/69971834/114399764-405ed800-9bdc-11eb-83c0-d79aa5c5cf6d.png">

# こだわり
・チャットを送信した際、画面に即表示される
・作成されたアカウントであればトークルームを作ることが可能


# 作成者
yuki.Echigawa

# 情報提供元
TECH CAMP
Thank you!

# テーブル設計

## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: room_users
- has_many :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user
