# 技術スタック

## 選定結果

| 層 | 技術 | 備考 |
|---|------|------|
| フロントエンド | Next.js | React Nativeへの展開を見据えて |
| バックエンド | Go (echo) | 軽量・高速・本番体験 |
| データベース | PostgreSQL | デファクトスタンダード |
| ホスティング | Oracle Cloud 無料枠 | ARM 4コア/24GB RAM/200GB 永続無料 |
| デプロイ | Docker + docker-compose | 本番構成の学習 |

## 開発ツール

| ツール | 選定 | 理由 |
|--------|------|------|
| Go フォーマッター | gofumpt | 厳格なルールでGoのイディオムを学習 |
| Go import管理 | gopls（LSP） | エディタ保存時に自動整理、手間なし |
| Go リンター | staticcheck（決定） | シンプル、Goチーム推奨 |
| Next.js フォーマッター | Biome | Rust製、高速、Prettier互換 |
| Next.js リンター | Oxlint | Rust製、超高速、ルール数豊富 |

## 選定理由

### フロントエンド: Next.js
- Reactベースでモバイルアプリ化（React Native）への展開が容易
- SSR/SSG対応、SEOにも強い
- 開発体験が良い

### バックエンド: Go (echo)
- 軽量・高速、リソース消費が少ない（無料VPSに最適）
- 静的型付けで堅牢
- シングルバイナリでデプロイが簡単
- 学習コストは高いが、その分得られるものが多い

### ホスティング: Oracle Cloud 無料枠
- ARM 4コア + 24GB RAM + 200GB 永続無料
- VPSを一から構築する本格的な体験
- Docker + docker-compose でデプロイ

### モバイルアプリ化
- React Native で Next.js と型・ロジックを共有可能
- APIはGoサーバーをそのまま利用