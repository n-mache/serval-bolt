# サーバル bot (Bolt 版)

[Bolt for JavaScript](https://github.com/slackapi/bolt-js) を利用したサーバル bot

## 機能

- いいね :+1: の数をカウントしてくれる
- 特定の数になると本人にたいして褒めてくれる
- 「いいねいくつ？」と聞くと自身のいいねの数を教えてくれる

## 実装予定の機能

- 入室時メッセージの表示

# 必要条件

- Node.js v14.17.2 以上
- TypeScript Version 4.3.5 以上
- PostgreSQL 12.7 以上

# DB の設定

`.env` ファイルに以下を記載、`DTABASE_URL` プロパティを設定。

```
# Environment variables declared in this file are automatically made available to Prisma.
# See the documentation for more detail: https://pris.ly/d/prisma-schema#using-environment-variables

# Prisma supports the native connection string format for PostgreSQL, MySQL, SQL Server and SQLite.
# See the documentation for all the connection string options: https://pris.ly/d/connection-strings

DATABASE_URL="postgresql://johndoe:randompassword@localhost:5432/serval_bolt?schema=public"
```

# DB の環境準備

```
npm i
npx prisma migrate dev --name init
```

# 起動方法

ソースコードの展開後、

```
npm i
npm run build
env SLACK_BOT_TOKEN="xoxb-0000000000000000000-000000000000000000" SLACK_APP_TOKEN="xapp-0-XXXXXXX-0000000000-XXXXXXXXXXXXXXX" npm start
```

以上で実行。

# Slack アプリケーションの作成方法

[https://qiita.com/seratch/items/1a460c08c3e245b56441](https://qiita.com/seratch/items/1a460c08c3e245b56441)
以上を参考に、WebSocket モードでアプリケーションを作成

## Event Subscription の設定

- message.channels
- member_left_channel (退出メッセージ機能の予定)
- member_joined_channel (入室メッセージ機能の予定)
- reaction_added (いいねのカウント機能)
- reaction_removed (いいねカウントの削除に対応の予定)

## Bot Token Scope の設定

- channels:history
- channels:read
- chat:write
- commands
- groups:read
- reactions:read

# Bolt のリファレンス

[https://slack.dev/bolt-js/ja-jp/reference](https://slack.dev/bolt-js/ja-jp/reference)