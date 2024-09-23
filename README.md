# README

## データベース設計

### usersテーブル

| カラム名          | 型        | 説明                                      |
|-------------------|-----------|-------------------------------------------|
| id                | BIGINT    | ユーザーID（主キー）                      |
| name              | STRING    | ユーザー名                                |
| email             | STRING    | メールアドレス（ユニーク）                |
| password_digest   | STRING    | パスワード（暗号化）                      |
| job               | STRING    | 勤務状態（常勤、非常勤）                  |
| role              | STRING    | 役職（研修医、専攻医、指導医など）        |
| skill             | STRING    | 指導可能なスキル（心臓麻酔、末梢神経ブロックなど）|
| created_at        | DATETIME  | 作成日                                    |
| updated_at        | DATETIME  | 更新日                                    |

## Association
- has_one :UserDailyInfo

### UserDailyInfosテーブル

| カラム名          | 型           | 説明                                      |
|-------------------|--------------|-------------------------------------------|
| id                | BIGINT       | ID（主キー）                              |
| user_id           | BIGINT       | 関連するユーザーID（外部キー）            |
| shift             | STRING       | 本日の勤務（早退、定時、当直など）        |
| status            | STRING       | ステータス（待機中、実施医、指導医など）  |
| operation_room    | INTEGER      | 実施医が選択した手術室番号（1〜25）       |
| operation_rooms   | INTEGER[]    | 指導医が選択した複数手術室番号（1〜25）   |
| round             | STRING       | ラウンド状況（ラウンド未、ラウンド済み）  |
| comment           | TEXT         | コメント                                  |
| created_at        | DATETIME     | 作成日                                    |
| updated_at        | DATETIME     | 更新日                                    |

## Association
- belongs_to :users
