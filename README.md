# chatspace DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|e-mail|string|null: false, unique:true|
|password|string|null: false|
### Association
- has_many :messages
- has_many :groups,  through:  :groups_users

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|title|string|null: false|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- has_many :message
- has_many :users,  through:  :groups_users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|integer|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
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