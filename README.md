# テーブル設計

## users テーブル

| Column          | Type   | Options     |
| --------------- | ------ | ----------- |
| nickname        | string | null: false |
| email           | string | null: false |
| password        | string | null: false |
| first_name      | string | null: false |
| last_name       | string | null: false |
| first_name_kana | string | null: false |
| last_name_kana  | string | null: false |
| birth_date      | string | null: false |

### Association

- has_many :users
- has_many :purchases

## items テーブル

| Column           | Type    | Options     |
| ---------------- | ------  | ----------- |
| user             | string  | null: false |
| name             | string  | null: false |
| description      | text    | null: false |
| image_id         | integer | null: false |
| category_id      | integer | null: false |
| condition_id     | integer | null: false |
| postage_payer_id | integer | null: false |
| prefecture_id    | integer | null: false |
| handing_time_id  | integer | null: false |
| price            | integer | null: false |

### Association

- has_many :users

## purchases テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| item   | references | null: false, foreign_key: true |
| user   | references | null: false, foreign_key: true |

### Association

- has_many :users
- belong_to :addresses

## addresses テーブル

| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| post_code      | string     | null: false                    |
| prefectures_id | integer    | null: false, foreign_key: true |
| city           | string     | null: false                    |
| building_name  | string     | null: false                    |
| phone_number   | string     | null: false, foreign_key: true |
| purchase       | references | null: false, foreign_key, true |

### Association

- belong_to :addresses
