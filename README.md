# 紹介用のリポジトリです  
[サービスURL]https://loving-beaver-3b1cb6.netlify.app/  
[フロントエンドリポジトリ]https://github.com/kbc18a11/AITalk_front  
[バックエンドリポジトリ]https://github.com/kbc18a11/AITalk_outApiCall_and_Auth

 
## 概要
誰でもAIのキャラクターを気軽に作成し、公開することができたらいいなと思い作成しました。

本物の会話型AIとチャットを通して、ログインなしで会話することができます。

キャラクターの口パクは、口を開けたものと口を閉じたものだけでいいため、高度なアニメーションを用意する必要がありません。またログインすれば、キャラクターにお気に入りやコメントをすることができます。

工夫した点は、認証にJWT、フロントエンドにReact.jsでSPAを構築し、アプリのような使用感を目指しました。また、NetlifyやJenkinsを利用して、GitをPushすると反応する自動デプロイを構築しました。
苦労した点は、フロントエンドの複雑化です。すべてJavaScriptで制御する必要があるため、コードやファイルの肥大化や型エラーに苦労しました。しかし、バリエーションにライブラリを使用したり、途中からTypeScriptを導入ことで、対策をしました。


## 動作方法
1. NobyAPIの利用登録を行ってください
2. AWSのS3を利用できるようにしてください
3. MySQLでデータベースを作成してください
4. バックエンドリポジトリからクローンしてください。
5. クローンしたリポジトリ内で、`composer install`を実行
6. リポジトリ内で、`php artisan jwt:secret`を実行し、表示されたトークをメモしてください。
7. バックエンドの設定ファイル(`.env.example`)の記述行ってください。  
```
APP_NAME=Laravel
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost

LOG_CHANNEL=stack

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=データベース名
DB_USERNAME=MySQLユーザー名
DB_PASSWORD=MySQLユーザーのパスワード

BROADCAST_DRIVER=log
CACHE_DRIVER=file
QUEUE_CONNECTION=sync
SESSION_DRIVER=file
SESSION_LIFETIME=120

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_MAILER=smtp
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS=null
MAIL_FROM_NAME="${APP_NAME}"

AWS_ACCESS_KEY_ID=AWSのアクセスキー
AWS_SECRET_ACCESS_KEY=AWSのシークレットキー
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=S3のバケット名

PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=
PUSHER_APP_CLUSTER=mt1

MIX_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
MIX_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"

NODY_API_APPKEY =NobyAPIのアプリケーションキー
NODY_API_MAIL =NobyAPIの利用登録した時のメールアドレス
NODY_API_PASS =NobyAPIの利用パスワード

JWT_SECRET= php artisan jwt:secretを実行して表示されたトークン

```
8. `php artisan serve`を実行
9. フロントエンドリポジトリからクローンしてください。
10. `npm install`を実行
11. `npm start`を実行
 
  
## 実装した機能
- AIモデル（AIのキャラクター）関係
  - 会話(チャット)機能
  - 作成、編集、削除機能
  - お気に入り登録機能
  - コメント機能(ページネーションで一覧表示)
  - 検索表示機能(ページネーションで一覧表示)
　  
   
- ユーザー関係
  - ユーザー登録、認証(ログイン、ログアウト)機能
  - ユーザー情報更新機能

　
## 利用した技術
- フロントエンド
  - 言語：Javascript，TypeScript
  - FW：React.js
  
  
- バックエンド(API)
  - 言語：PHP
  - FW：Laravel
- データベース
  - MySQL(RDS)
  
  
- インフラ
  - フロントエンド関係：Netlify
  - バックエンド関係：AWS(Route53，ACM，ALB，EC2(Amazon Linux2))，Jenkins
  
- 外部API
  - S3(ファイルストレージ)
  - Noby API (会話型AI)
