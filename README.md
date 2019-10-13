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

# Chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false,unique: true|
|password|string|null: false|
|name|string|null: false|

### Association
- has_many :messages
- has_many :groups_users
- has_many :groups, through: :groups_users


## messages テーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group_id|integer|null: false,add_foreign_key|
|user_id|integer|null: false,add_foreign_key|

### Asociation
- belongs_to :user
- belongs_to :group

## groups テーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|

### Asociation
- has_many :masseges
- has_many :groups_users
- has_many :users, thorough: :groups_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, add_foreign_key|
|group_id|integer|null: false, add_foreign_key|

### Association
- belongs_to :group
- belongs_to :user