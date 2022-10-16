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
    - [service](#service-1)
    - [controller](#controller-1)
- [rspec](#rspec)

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
  - ex) `app/controllers/adminA/tasks_controller.rb`
  - ex) `app/controllers/adminB/tasks_controller.rb`

※管理画面用のアカウント種別によって異なる権限を付与できる

#### コード例

```rb

```

### view

- `app/views/権限名/ドメイン名複数系/アクション名.rb`

# api

### model

### service

### controller

# rspec
