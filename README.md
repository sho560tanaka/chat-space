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

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|index: true, null: false, unique: true|
### Association
- has_many :messages
- has_many :members
- has_many :groups, through: :groups_users


## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false,unigue: true|
### Association
- has_many :users,through: :groups_users
- has_many :messages

## massagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|user_id|integer|null: false,foreign_key: true|
|group_id|integer|null: false,foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false,foreign_key: true|
|group_id|integer|null: false,foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user