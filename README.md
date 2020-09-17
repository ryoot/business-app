# テーブル設計

## users テーブル

| Column          | Type    | Options     |
| --------------- | ------- | ----------- |
| nickname        | string  | null: false |
| email           | string  | null: false |
| password        | string  | null: false |
| first-name      | string  | null: false |
| family-name     | string  | null: false |
| first-name-kana | string  | null: false |
| family-name-kana| string  | null: false |
| gender          | string  | null: false |
| birthday        | date    | null: false |

### Association
- has_many :chat-room
- has_many :items

## items テーブル

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| name             | string     | null: false                    |
| image            | string     | null: false                    |
| text             | string     | null: false                    |


### Association

- belongs_to :user

## chat-rooms テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |

### Association

- belongs_to :user

##  chat-room-usersテーブル

| Column            | Type       | Options                        |
| ----------------- | ---------- | ------------------------------ |
| user_id           | references | null: false, foreign_key: true |
| chat-room_id      | references | null: false, foreign_key: true |

### Association

- has_many :messages
- belongs_to :user
- belongs_to :chat-room

## chat-message テーブル
| Column         | Type           | Options                        |
| ------------- -| -------------- | ------------------------------ |
| user_id        | references     | null: false                    |
| chat-room_id   | string         | null: false                    |
| message        | string         | null: false                    |

### Association
- belongs_to :chat-room