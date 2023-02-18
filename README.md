# 目次

<!-- TOC -->

- [目次](#目次)
- [概要](#概要)
- [構成](#構成)
  - [model](#model)
    - [注意点](#注意点)
  - [controller](#controller)
    - [管理画面](#管理画面)
    - [API](#api)
  - [view](#view)
    - [管理画面](#管理画面-1)
    - [API](#api-1)
  - [JavaScript（管理画面用）](#javascript管理画面用)
  - [rspec](#rspec)
  - [seed](#seed)
  - [batch](#batch)
  - [Gemfile](#gemfile)
    - [よく使うもの](#よく使うもの)
      - [全体](#全体)
      - [development](#development)
      - [development, test](#development-test)
    - [注意点](#注意点-1)
  - [テスト戦略](#テスト戦略)

<!-- /TOC -->

# 概要

- フロントエンド → 別アプリケーション。monorepo、マイクロサービス想定。
- 基本的に本リポジトリで表示する view は管理画面のみ。

# 構成

## model

- `app/models/ドメイン名単数系.rb`
  - ex) `app/models/task.rb`

→ 肥大化しそうなら service 層を作成し、ロジックを逃すなど検討しても良い。

### 注意点

devise の設計に合わせないなら users テーブルと devise 用のテーブルを分ける（大体分けた方が良い）  
User の情報と devise で必要な認証情報でバリデーションがバッティングして、仕様通りの実装が出来なくなる可能性がある。  
User モデルの子モデルに、UserAuthenticate モデルと、UserProfile モデルを作るのがスマート[（参考）](https://qiita.com/hatsu/items/5393a09e630de043f574)。

## controller

### 管理画面

- `app/controllers/権限名/ドメイン名複数系_controller.rb`
  - ex) `app/controllers/admin/tasks_controller.rb`
  - ex) `app/controllers/owner/tasks_controller.rb`
  - ex) `app/controllers/staff/tasks_controller.rb`

※管理画面用のアカウント種別によって異なる権限を付与できる  
→ DB のレコードによって権限を分ける方法もあり。

### API

- `app/controllers/api/バージョン/ドメイン名複数系_controller.rb`
  - ex) `app/controllers/api/v1/tasks_controller.rb`

## view

### 管理画面

- `app/views/権限名/ドメイン名複数系/アクション名.html.erb`
  - ex) `app/views/admin/tasks/index.html.erb`

### API

- `app/views/api/バージョン/ドメイン名複数系/アクション名.html.erb`
  - ex) `app/views/api/v1/tasks/show.html.erb`

API から HTML を返す時のみ利用

## JavaScript（管理画面用）

- `app/packs/application.js` → 下記のファイルを import する
- `app/javascript/ドメイン名単数系.js` → JS 処理を記述

## rspec

rspec デフォルトのディレクトリを使う。

## seed

- `db/seeds.rb`
  → seeds コマンドで実行される
- `db/seed/モデル名単数系.rb`
  → モデル毎に分ける。共通のものもは `common.rb`などとするのが一般的。

## batch

- `app/batches/処理名.rb`

## Gemfile

### よく使うもの

#### 全体

- `jbuilder` 必要なら
- `bootstrap` 管理画面用
- `kaminari` ページネーション
- `rack-cors` CORS
- `mysql2` など利用する db に合わせた gem を入れる
- `devise_token_auth` api での user 認証で
- `devise` 管理画面でのでの user 認証で
- `devise-i18n` devise の文言を設定する
- `rails-i18n` 全体でエラーなどの文言を設定する
- `active_hash` or `config` 定数。active_hash は active record の様に操作できて便利
- `dotenv-rails` 環境変数用に
- `ransack` 検索用に
- `aws-sdk-3s`, `carrierwave`, `fog-aws` など 画像アップロード機能
- `business_time` など祝日管理用に使う

#### development

- `byebug` か `pry-byebug`、環境が許すなら pry の方が便利
- `letter_opener_web` メール送信機能の確認

#### development, test

- `rubocop` 静的解析
- `rubocop-rails` 静的解析
- `rubocop-rspec` 静的解析
- `rspec-rails` テスティングフレームワーク
- `gimei` テストデータの日本人名を作成
- `factory_bot_rails` テストデータ作成

### 注意点

- `webpaker` より `webpack` が望ましい

## テスト戦略

- model
  - 実行も重く無いのでカバレッジ重視してできるだけ多くする
- requests
  - テストケースを練ってケース数を増やしすぎない（複数の expect を書いて it は最小限）

# 参考になるリポジトリ
- Railsのみ： https://github.com/rubygems/rubygems.org
- Rails x React: https://github.com/kazama1209/rails-react-todo
- Rails x Vue: https://github.com/K-kind/Punct
