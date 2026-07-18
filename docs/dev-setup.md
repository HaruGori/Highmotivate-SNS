# 開発環境構築

## 構成

```
Highmotivate-SNS/
├── frontend/          # Next.js
├── backend/           # Go (echo)
├── docker-compose.yml # PostgreSQL + 各サービス
└── .env.example       # 環境変数サンプル
```

## ローカル開発

### 前提

- Go 1.23+
- Node.js 22+
- Docker Desktop

### 起動方法

```bash
# DBのみDockerで起動
docker compose up db -d

# バックエンド起動（ホットリロード）
cd backend && go run .

# フロントエンド起動（別ターミナル）
cd frontend && npm run dev
```

### 全体をDockerで起動

```bash
docker compose up --build
```

- フロントエンド: http://localhost:3000
- バックエンドAPI: http://localhost:8080
- ヘルスチェック: http://localhost:8080/api/health

## 環境変数

`.env.example` をコピーして `.env` を作成する。

```bash
cp .env.example .env
```

## リンター・フォーマッター設定

### Go（ backend/）

```bash
# フォーマッター（gofumpt）
go install mvdan.cc/gofumpt@latest

# リンター（staticcheck）
go install honnef.co/go/tools/cmd/staticcheck@latest
```

### VSCode 設定（.vscode/settings.json）

```json
{
  "go.useLanguageServer": true,
  "gopls": {
    "formatting.gofumpt": true
  },
  "go.lintTool": "staticcheck",
  "go.lintFlags": ["-checks=all,-ST1000"],
  "[go]": {
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.organizeImports": true
    }
  }
}
```

### Next.js（ frontend/）

```bash
# フォーマッター: Biome / リンター: Oxlint
npm run format   # Biome で整形
npm run lint     # Oxlint でチェック
```