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

# テスト戦略

- model
  - 実行も重く無いのでカバレッジ重視してできるだけ多くする
- requests
  - テストケースを練ってケース数を増やしすぎない
