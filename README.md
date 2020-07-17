# ProjectDo:App Database Design

## users table

|Column|Type|Options|
|------|----|-------|
|name|string|null:false|
|icon|string|null:false|
|email|string|null:false, unique: true|
|password|string|null:false|

### Association

- has_many :tasks
- has_many :groups, through: :user_groups

## tasks table

|Column|Type|Options|
|------|----|-------|
|title|string|null:false|
|target_at|datetime|null:true|
|completed_at|datetime|null:false|
|completed|boolean|
|user_id|integer|null: false,foreign_key: true|
## Association
- belongs_to :user
- belongs_to :group
## groups table
|Column|Type|Option|
|------|----|------|
|project|string|null:false, unique: true|
### Association
- has_many :task
- has_many :users, through: :user_groups
## user_groups table
|Column|Type|Option|
|------|----|------|
|user_id|integer|null:false, foreign_key:true|
|group_id|integer|null:false, foreign_key:true|
### Association
- belongs_to :user
- belongs_to :group
