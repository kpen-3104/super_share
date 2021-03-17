# テーブル設計

## users テーブル

| Column          | Type    | Options                  |
| --------------- | ------- | ------------------------ |
| employee_cord   | integer | null: false              |
| last_name       | string  | null: false              |
| fast_name       | string  | null: false              |
| last_name_kana  | string  | null: false              |
| first_name_kana | string  | null: false              |
| email           | string  | null: false              |
| password        | string  | null: false              |
| position        | integer | null: false              |
| department      | integer | null: false              |
| store           | integer | null: false              |


### Association
- has_many :topics
- has_many :posts

## topics テーブル

| Column | Type       | Options                      |
| ------ | ---------- | ---------------------------- |
| topic  | string     | null: false                  |
| user   | reference  | null: false foreign_key: true|


### Association

- belongs_to :user
- has_many :posts
- has_many :topic_tags
- has_many :tags, through: :topic_tags

## posts テーブル

| Column   | Type       | Options                      |
| -------- | ---------- | ---------------------------- |
| title    | string     | null: false                  |
| content  | string     | null: false                  |
| user     | references | null: false foreign_key: true|
| topic    | references | null: false foreign_key: true|

### Association

- belongs_to :user
- belongs_to :topic

##  tagsテーブル

| Column       | Type        | Options                      |
| ------------ | ----------- | ---------------------------- |
| store        | integer     | null: false                  |
| department   | integer     | null: false                  |

### Association

- has_many :topic_tag 
- has_many :topic, through: :topic_tag

##  topic_tagsテーブル

| Column  | Type          | Options                             |
| ------- | ------------- | ----------------------------------- |
| topic   | references    | null: false false foreign_key: true |
| tag     | references    | null: false false foreign_key: true |

### Association

- belongs_to :topic
- belongs_to :tag
