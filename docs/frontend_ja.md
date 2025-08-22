# PullLog Frontend Documentation

PullLog フロントエンドは、**個人のガチャ履歴を記録・分析する Web アプリケーション**のクライアント側実装です。  
Nuxt.js 3 をベースに SSR (Server-Side Rendering) + API プロキシ構成を採用し、快適な UI/UX と多言語対応を提供します。

---

## 主な特徴

- ガチャ履歴（タイトル・日付・回数・最高レア・課金額・タグ等）の登録・管理
- PrimeVue ベースの UI コンポーネント
- Luxon を用いたタイムゾーン対応
- Chart.js による統計グラフ（回数推移・課金推移など）
- Zod を用いた型安全なフォームバリデーション
- ダーク／ライトテーマ切り替え
- 多言語対応（日本語 / 英語 / 中国語）
- Google アカウントによるソーシャルログイン
- バックエンド API との連携（認証付き、API プロキシ経由）

---

## 技術スタック

- **フレームワーク**: Nuxt.js v3
- **UI**: PrimeVue v4, TailwindCSS v4, SCSS
- **状態管理**: Pinia v3
- **言語**: TypeScript
- **日付管理**: Luxon
- **グラフ描画**: Chart.js
- **バリデーション**: Zod
- **その他**: SortableJS, Marked, ESLint, TypeDoc

---

## 設計・開発指針

### 状態管理と責務分離
- Pinia ストアを用途ごとに分離し、責務を限定
  - `useUserStore`: 認証・ユーザー情報
  - `useAppStore`: アプリケーション情報
  - `useLogStore`: ガチャ履歴の取得・キャッシュ
  - `useStatsStore`: 統計データ管理
  - `useOptionStore`: ユーザー設定・選択肢
  - `useCsrfStore`: CSRF トークン管理
  - `useLoaderStore`: ローディング状態
  - `useCurrencyStore`: 通貨データ管理
  - `globalStore`: グローバル値の一時保持
- キャッシュは必要最小限。空配列やエラー時データのキャッシュは禁止。

### 型安全とコーディング規約
- すべて TypeScript で実装。`any` および非 null アサーション（`!`）は原則禁止。
- インデントは 4 スペース。セミコロンは不要。
- 型定義は `types/` に集約し、JSDoc コメントは TypeDoc 準拠。

### 日付と国際化
- Luxon により ISO8601/Date 型で厳密に管理。
- i18n を利用し、UI 文言は `t()` メソッドを通して管理。

### グラフ描画
- Chart.js をラップした共通コンポーネントを提供。
- テーマ切り替え時にリアルタイム反映。

### バリデーション
- PrimeVue の Form コンポーネントは利用せず、Zod による型安全なバリデーションを採用。

### スタイリング
- 基本設計は TailwindCSS、詳細調整は SCSS。
- コンポーネント内に `scoped` スタイルは原則書かず、PassThrough API や SCSS で統一管理。

---

## デプロイ・ホスティング

- フロントエンドは SSR 構成を採用しており、**Cloudflare Workers 上でホスティング**されます。
- API リクエストはすべて Nuxt (Nitro) サーバの **API プロキシ経由**でバックエンド Laravel API へ転送されます。
- 開発環境と本番環境の API エンドポイントは `.env` および `runtimeConfig` で切り替え可能。

---

## 関連リンク

- [PullLogバックエンド概要](./backend_ja.md)
- [PullLog API仕様](../docs/api/overview.md)
- [利用規約](../public/docs/terms_ja.md)  
- [プライバシー・ポリシー](../public/docs/privacy_policy_ja.md)

---
