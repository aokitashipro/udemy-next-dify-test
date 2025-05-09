Udemy講座 

【Next.js】【DifyAPI】認証・継続課金機能付きの生成AIアプリをハンズオンで開発してみよう

の公開コードになります。

https://www.udemy.com/course/nextjsdifyapi/

## インストール手順

git clone git@github.com:aokitashipro/udemy-next-dify-test.git

cd udemy-next-dify-test

npm install

.env 作成

DIFY側で作成・取得したURLやAPIキーを記載します。

DIFY_API_URL=http://localhost/v1

DIFY_API_KEY=xxx

## Prismaの設定

npx prisma init # Prismaの初期化

prisma/schema.prisma の設定

provider="sqlite" に変更

.envファイル

postgresqlはコメントアウト

DATABASE_URL="file:./dev.db" # 追記

## マイグレーションとシード実行

npx prisma migrate dev --name init # Prismaクライアント作成・テーブル作成

npx prisma db seed # シード実行

npx prisma studio # DBの内容を確認

## Auth.jsの設定

npx auth secret # シークレットキー生成

.env.localにAUTH_SECRETが発行されるので、.envに統合

## うまくいかない時のおまじない

キャッシュクリア

rm -rf .next

rm -rf node_modules/.prisma

依存関係の再インストール

npm install

Prismaクライアントの再生成

npx prisma generate

キャッシュなしでビルド

npm run build -- --no-cache

