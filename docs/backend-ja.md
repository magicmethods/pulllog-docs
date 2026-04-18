# PullLog Backend ドキュメント

## 概要

PullLog Backend は、個人のガチャ履歴を記録・管理する Web アプリ PullLog のバックエンド部分です。  
フロントエンドとデータベースの間で API を通じたデータ中継を担い、リクエストに応じて JSON を返します。

- バックエンドは Laravel と PostgreSQL を基盤技術としています
- 初期開発や検証ではモック環境を利用する場合があります
- 認証、セッション管理、統計処理、画像処理を含みます

---

## 主な機能

- RESTful API 形式で JSON レスポンスを返却
- ユーザー認証、トークン管理、CSRF セッションの検証
- ユーザーごとの履歴データの保存と集計
- 通貨単位や小数桁数に応じた課金データ処理
- 統計キャッシュによる効率的な分析処理

---

## 技術スタック

- 言語: PHP v8 系
- フレームワーク: Laravel 12
- データベース: PostgreSQL
- モック環境: MockAPI-PHP
- 画像処理: Intervention Image
- 開発用メール送信: mailtrap

---

## データと実行構成の概要

- バックエンドは PostgreSQL 上でユーザー、アプリ、履歴、統計、認証、ギャラリー関連データを管理します
- `logs` 領域ではパーティションや補助ビューを用いた設計を採用しています
- 詳細なスキーマ、ER 図、デプロイ設定、APP_KEY / API_KEY の扱い、モック接続手順は backend subproject の文書を正本とします

## 正本参照

- バックエンド構成と実装方針: `backend/docs/architecture/overview.md`
- デプロイ / ロールバック手順: `backend/docs/operations/deploy-and-release.md`
- サービス運用の正本概要: `backend/docs/operations/service-operations-overview.md`
- セットアップ、モック環境、横断メモ: `backend/README.md`

この公開文書では、環境依存セットアップ、秘密情報生成、モック接続設定、デプロイ設定の詳細は扱いません。

---

## ライセンス

MAGIC METHODS に帰属します。

---

## コントリビューション

- Pull Request や Issue を歓迎します
- 設計や方針の議論は Discussions または Issue で行ってください
- セキュリティ報告は一般 Issue ではなく support@pulllog.net へ連絡してください

---

## 関連リンク

- [PullLogフロントエンド概要](./frontend-ja.md)
- [PullLog API概要](./api-overview-ja.md)
- [利用規約](../public/terms.md)
- [プライバシー・ポリシー](../public/privacy.md)

---