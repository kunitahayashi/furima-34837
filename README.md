# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

>>>>>>>>>>>>>>>>>>>>>


## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| nickname          | string | null: false |
| encrypted_password| string | null: false |
| email             | string | null: false |
| myouji_kanji      | string | null: false |
| namae_kanji       | string | null: false |
| myouji_katakana   | string | null: false |
| namae_kanji       | string | null: false |
| seinenngappi      | date   | null: false |




////Association////

- has_many :items
- has_many :addresses
- has_many :purchases

## 配送先住所 テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| postal-code       | string | null: false |
| address1_id       | integer| null: false |
| address2          | string | null: false |
| address3          | string | null: false |
| address4          | string | null: false |
| phone-number      | string | null: false |
| purchases         | references | null: false, foreign_key: true |


////Association////

- belongs_to :user
- belongs_to :item
- belongs_to :purchase


## items テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| price        |integer    | null: false |
| user         | reference |null: false, foreign_key: true |
| item         | string    | null: false |
| explanation  | text      | null: false |
| category_id  | integer   | null: false |
| status_id    | integer   | null: false |
| fee_id       | integer   | null: false |
| address1_id  | integer   | null: false |
| days_required| integer   | null: false |


////Association////

- belongs_to :addresses
- belongs_to :purchase
- belongs_to :user



## purchases テーブル


| Column | Type   | Options     |
| ------ | ------ | ----------- |
| user  | references | null: false, foreign_key: true |
| item  | references | null: false, foreign_key: true |

////Association////

- belongs_to :item
- belongs_to :user
