# API設計

ベースURL: `http://localhost:8080/api`

## 認証

| Method | Path | 説明 |
|--------|------|------|
| POST | /api/auth/signup | メール登録 |
| POST | /api/auth/login | メールログイン |
| POST | /api/auth/google | Googleログイン |
| POST | /api/auth/logout | ログアウト |

## ユーザー

| Method | Path | 説明 |
|--------|------|------|
| GET | /api/users/:id | プロフィール取得 |
| PUT | /api/users/:id | プロフィール更新 |
| GET | /api/users/:id/posts | ユーザーのエール一覧 |
| GET | /api/users/:id/likes | ユーザーのがんば！一覧 |
| GET | /api/users/:id/cheers | ユーザーの応援一覧 |
| GET | /api/users/search?q= | ユーザー検索 |

## フォロー

| Method | Path | 説明 |
|--------|------|------|
| POST | /api/users/:id/follow | フォロー |
| DELETE | /api/users/:id/follow | フォロー解除 |
| GET | /api/users/:id/followers | フォロワー一覧 |
| GET | /api/users/:id/following | フォロー中一覧 |

## エール（投稿）

| Method | Path | 説明 |
|--------|------|------|
| GET | /api/posts | タイムライン（フォロー中） |
| GET | /api/posts/explore | おすすめ |
| POST | /api/posts | エール作成 |
| GET | /api/posts/:id | エール詳細 |
| DELETE | /api/posts/:id | エール削除 |

## インタラクション

| Method | Path | 説明 |
|--------|------|------|
| POST | /api/posts/:id/like | がんば！ |
| DELETE | /api/posts/:id/like | がんば！解除 |
| POST | /api/posts/:id/cheer | 応援 |
| DELETE | /api/posts/:id/cheer | 応援解除 |
| POST | /api/posts/:id/repost | リエール |
| DELETE | /api/posts/:id/repost | リエール解除 |
| GET | /api/posts/:id/comments | コメント一覧 |
| POST | /api/posts/:id/comments | コメント投稿 |

## タグ

| Method | Path | 説明 |
|--------|------|------|
| GET | /api/tags | タグ一覧 |
| GET | /api/tags/:name/posts | タグ別エール一覧 |

---

## リクエスト/レスポンス例

### POST /api/auth/signup

```json
// Request
{ "username": "taro", "email": "taro@example.com", "password": "password123" }

// Response 201
{ "id": "uuid", "username": "taro", "display_name": "taro" }
```

### POST /api/auth/login

```json
// Request
{ "email": "taro@example.com", "password": "password123" }

// Response 200
{ "token": "jwt_token", "user": { "id": "uuid", "username": "taro" } }
```

### POST /api/posts

```json
// Request
{ "content": "今日の目標：筋トレ30分！", "post_type": "goal", "tags": ["筋トレ"] }

// Response 201
{ "id": "uuid", "content": "今日の目標：筋トレ30分！", "post_type": "goal", "tags": ["筋トレ"], "likes_count": 0, "cheers_count": 0, "comments_count": 0, "created_at": "2026-07-20T00:00:00Z" }
```

### GET /api/posts

```json
// Response 200
{ "posts": [{ "id": "uuid", "user": { "id": "uuid", "username": "taro", "display_name": "taro", "avatar_url": null }, "content": "今日の目標：筋トレ30分！", "post_type": "goal", "tags": ["筋トレ"], "likes_count": 5, "cheers_count": 3, "comments_count": 2, "is_liked": false, "is_cheered": false, "created_at": "2026-07-20T00:00:00Z" }], "cursor": "next_cursor" }
```