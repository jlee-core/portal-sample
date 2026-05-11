# セットアップ手順

## 必要環境

事前に以下をインストールしてください。

- Docker Desktop
- PHP
- Composer
- Node.js / npm

---

# 初期セットアップ

リポジトリを clone 後、プロジェクトディレクトリへ移動します。

```bash
git clone git@github.com:jlee-core/portal-sample.git
cd portal-sample
```

Docker Desktop を起動します。

```bash
open -a Docker
```

依存関係をインストールします。

```bash
composer install
```

Laravel Sail を起動します。

```bash
./vendor/bin/sail up -d
```

セットアップコマンドを実行します。

```bash
composer run setup
```

---

# 開発環境の起動

開発サーバーを起動します。

```bash
composer run dev
```

以下のサービスが同時に起動します。

- Laravel Queue Worker
- Laravel Pail
- Vite Development Server

---

# よく使うコマンド

## Sail を停止

```bash
./vendor/bin/sail down
```

## Queue Worker の再起動

```bash
./vendor/bin/sail artisan queue:restart
```

## マイグレーション実行

```bash
./vendor/bin/sail artisan migrate
```

## コンテナ内に入る

```bash
./vendor/bin/sail shell
```

---

# Docker が起動しているか確認

Sail コマンドが動作しない場合は、Docker Desktop が起動しているか確認してください。

```bash
docker ps
```

---

# Sail エイリアス設定（任意）

毎回 `./vendor/bin/sail` を入力するのが面倒な場合は、エイリアス設定をおすすめします。

```bash
alias sail='sh $([ -f sail ] && echo sail || echo vendor/bin/sail)'
```

設定後は以下のように短縮して実行できます。

```bash
sail up -d
```