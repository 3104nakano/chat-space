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
|name|string|null: false,index: true|

### Association
- has_many :messages
- has_many :group_users
- has_many :groups, through: :group_users


## messages テーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group|references|null: false,foreign_key: true|
|user|references|null: false,foreign_key: true|

### Asociation
- belongs_to :user
- belongs_to :group

## groups テーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|


### Asociation
- has_many :masseges
- has_many :group_users
- has_many :users, thorough: :group_users

## group_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user