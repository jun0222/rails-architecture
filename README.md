# 目次

<!-- TOC -->

- [目次](#目次)
- [管理画面](#管理画面)
  - [ディレクトリ構成](#ディレクトリ構成)
    - [model](#model)
      - [コード例](#コード例)
    - [service](#service)
    - [controller](#controller)
      - [コード例](#コード例-1)
    - [view](#view)
- [api](#api)
  - [model](#model-1)
  - [services](#services)
  - [controller](#controller-1)
- [rspec](#rspec)
- [Gemfile](#gemfile)
  - [よく使うもの](#よく使うもの)
    - [全体](#全体)
    - [development](#development)
    - [development, test](#development-test)
  - [注意点](#注意点)
- [テスト戦略](#テスト戦略)

<!-- /TOC -->

# 管理画面

## ディレクトリ構成

### model

- `app/models/ドメイン名単数系.rb`
  - ex) `app/models/task.rb`

#### コード例

```rb

```

### service

### controller

- `app/controllers/権限名/ドメイン名複数系_controller.rb`
  - ex) `app/controllers/admin/tasks_controller.rb`
  - ex) `app/controllers/owner/tasks_controller.rb`
  - ex) `app/controllers/staff/tasks_controller.rb`

※管理画面用のアカウント種別によって異なる権限を付与できる  
→ DB のレコードによって権限を分ける方法もあり。メリットデメリット

#### コード例

```rb

```

### view

- `app/views/権限名/ドメイン名複数系/アクション名.rb`

# api

### model

※devise の設計に合わせないなら users テーブルと devise 用のテーブルを分ける（大体分けた方が良い）

### services

※ここにバリデーションを書く

### controller

# rspec

# Gemfile

## よく使うもの

### 全体

- `jbuilder` 必要なら
- `bootstrap` 管理画面用
- `kaminari` ページネーション
- `rack-cors` CORS
- `mysql2` など利用する db に合わせた gem を入れる
- `devise_token_auth` api での user 認証で
- `devise` 管理画面でのでの user 認証で
- `devise-i18n` devise の文言を設定する
- `rails-i18n` 全体でエラーなどの文言を設定する
- `active_hash` or config 定数。active_hash は active record の様に操作できて便利
- `dotenv-rails` 環境変数用に
- `ransack` 検索用に
- `aws-sdk-3s`, carrierwave, fog-aws など 画像アップロード機能
- `business_time` など祝日管理用に使う

### development

- `byebug` か `pry-byebug`、環境が許すなら pry の方が便利
- `letter_opener_web` メール送信機能の確認

### development, test

- `rubocop` 静的解析
- `rubocop-rails` 静的解析
- `rubocop-rspec` 静的解析
- `rspec-rails` テスティングフレームワーク
- `gimei` テストデータの日本人名を作成
- `factory_bot_rails` テストデータ作成

## 注意点

- `webpaker` より `webpack` が望ましい

# テスト戦略

- model
  - 実行も重く無いのでカバレッジ重視してできるだけ多くする
- requests
  - テストケースを練ってケース数を増やしすぎない
