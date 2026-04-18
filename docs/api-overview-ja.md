# PullLog API 概要

この文書は PullLog バックエンド API の公開向け高水準概要です。  
バージョン管理、認証、主要リソース群、および正本契約との関係を要約します。

> 注意  
> 機械可読な契約正本は contract subproject の `contract/api-schema.yaml` で管理されます。  
> このページは概要に限定し、完全な契約内容は再掲しません。

---

## 公開概要

- PullLog API はバージョン管理された contract-driven API です
- 主なリソース群は auth、apps、logs、stats、user、gallery です
- 通常のブラウザアクセスは公式 frontend のサーバー側プロキシを経由します

この公開ページは簡潔さを優先しています。人が読むためのルート概要や契約保守手順は contract subproject 側の文書を正本とします。

## 正本参照

- 人間向け API 概要正本: `contract/docs/api-overview.md`
- 機械可読な正本: `contract/api-schema.yaml`
- 契約保守ワークフロー: `contract/docs/api-contract-sync-workflow.md`

## 公開利用上の注意

- 通常のブラウザ利用では公式 frontend を利用してください
- リクエスト / レスポンス構造の正確な定義は `contract/api-schema.yaml` を正本としてください
- ルート群の整理やレビュー手順は contract subproject の文書を正本としてください

## 関連リンク

- `./backend-ja.md`
- `./frontend-ja.md`

---