# PullLog Frontend Documentation

PullLog フロントエンドは、個人のガチャ履歴を記録・分析する Web アプリケーションのクライアント側実装です。  
Nuxt.js 3 をベースに SSR と API プロキシ構成を採用し、快適な UI と多言語対応を提供します。

---

## 主な特徴

- ガチャ履歴の登録と管理
- PrimeVue ベースの UI コンポーネント
- Luxon によるタイムゾーン対応
- Chart.js による統計グラフ表示
- Zod を利用した型安全なフォームバリデーション
- ダーク / ライトテーマ切り替え
- 日本語 / 英語 / 中国語の多言語対応
- Google アカウントによるソーシャルログイン
- バックエンド API との連携をサーバー側プロキシ経由で実施

---

## 技術スタック

- フレームワーク: Nuxt.js v3
- UI: PrimeVue v4, TailwindCSS v4, SCSS
- 状態管理: Pinia v3
- 言語: TypeScript
- 日付管理: Luxon
- グラフ描画: Chart.js
- バリデーション: Zod
- その他: SortableJS, Marked, ESLint, TypeDoc

---

## アーキテクチャ概要

- フロントエンドは Nuxt 3 SSR を採用し、Cloudflare Workers 上で稼働します。
- ブラウザからの API 通信は Nuxt の API プロキシを経由してバックエンドへ転送されます。
- 型安全な実装、国際化、バリデーション、グラフ描画などの詳細設計は frontend subproject 側の文書を正本とします。

ストア分割、型配置、middleware、runtimeConfig、API プロキシの具体方針は frontend subproject の技術文書を参照してください。

## 正本参照

- フロントエンドの技術構成と実装方針: `frontend/docs/architecture/overview.md`
- フロントエンドのビルド / デプロイ手順: `frontend/docs/operations/deploy-and-build.md`
- API 契約の正本: `contract/api-schema.yaml`

---

## 公開 E2E テスト概要

フロントエンドでは、重要なユーザーフローを検証するための manifest-driven な Playwright E2E テストアーキテクチャも運用しています。

### 公開可能な特性

- 規定デバイスマトリクス:
  - `chromium`: PC
  - `ipad-pro-11`: タブレット
  - `iphone-14`: スマートフォン
- ケース定義は JSON マニフェストで管理
- すべての E2E 実行で Markdown レポートを生成
- 成功時は PDF evidence としてアーカイブ可能
- 共有テンプレートと PullLog 専用テンプレートセットに対応

### レポーティング方針

- 1 つの case id は 1 つの論理シナリオを表します
- 同じ case を複数プロジェクト / デバイスで実行した場合、ケースレポートには実行された全プロジェクトの結果を集約表示します
- PDF evidence では PC / Tablet / Smartphone の比較表と、各プロジェクト詳細を併記できます

この公開文書では概要のみを扱い、認証情報、内部エンドポイント、運用専用の詳細は掲載しません。

---

## 関連リンク

- [PullLogバックエンド概要](./backend-ja.md)
- [PullLog API概要](./api-overview-ja.md)
- [利用規約](../public/terms.md)
- [プライバシー・ポリシー](../public/privacy.md)

---