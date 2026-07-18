# 技術スタック

## 選定結果

| 層 | 技術 | 備考 |
|---|------|------|
| フロントエンド | Next.js | React Nativeへの展開を見据えて |
| バックエンド | Go (echo) | 軽量・高速・本番体験 |
| データベース | PostgreSQL | デファクトスタンダード |
| ホスティング | Oracle Cloud 無料枠 | ARM 4コア/24GB RAM/200GB 永続無料 |
| デプロイ | Docker + docker-compose | 本番構成の学習 |

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