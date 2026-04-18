# Repository Guidelines

本ドキュメントは `pulllog-docs/`（公開ドキュメント）向けの作業ガイドです。
このワークスペースは主に Markdown 資産を扱います。

## Terminology Policy
- PullLog 全体は `workspace`、`frontend/` `backend/` `contract/` `pulllog-docs/` など各トップレベルディレクトリは `subproject` と呼ぶ。
- 正式な定義は `docs/workspace-terminology.md` を参照する。
- VS Code 機能や pnpm の説明では、それぞれの公式用語を優先する。

## Project Structure
- `docs/`: 技術ドキュメント本文（architecture / frontend / backend / ops / api overview）
- `public/`: 公開ポリシー文書や画像・動画アセット
- `README.md`, `ROADMAP.md`, `CHANGELOG.md`, `SECURITY.md`: ルート文書
- `.github/agents/`: 文書監査と運用保守のカスタムエージェント定義
- `.github/ISSUE_TEMPLATE/`: Issue テンプレート

## Documentation Governance
- PullLog 全体の文書ガバナンス正本は `docs/document-governance.md` を参照する。
- `pulllog-docs/` は共有用語、公開ドキュメント方針、横断文書監査ワークフローを管理する。
- 各 subproject の技術的な正本は各 subproject 側に残し、`pulllog-docs/` が勝手に上書きしない。

## Editing Policy
- 変更はユーザー依頼範囲に限定する。
- 公開情報のみ扱い、秘密情報・内部エンドポイント・認証情報を記載しない。
- 既存のトーンと文体を維持し、無関係な大規模リライトを避ける。
- 画像・動画パスは既存の相対パス規約に合わせる。
- 壊れたリンクや誤字を見つけた場合は、影響範囲が明確なら同時に修正してよい。

## Validation Policy
- Markdown 変更時は最低限リンク整合性と参照パスを確認する。
- コード生成やビルドが不要な変更では、不要なコマンド実行を行わない。

## Security & Publication Notes
- `SECURITY.md` の方針に従い、脆弱性情報は適切な経路で報告する。
- 公開資料に機密情報を含めない。

## Agent-Specific Notes
- 本 AGENTS.md は `pulllog-docs/` 配下に適用。

## Workspace Root Policy Summary
- 上位階層（`pulllog/AGENTS.md`）の共通方針に合わせ、Windows では PowerShell を優先する。
- Python は存在を前提にしない。未確認状態で Python スクリプトを生成・実行しない。
- 実行コマンドは以下を優先する: リポジトリ内既存スクリプト → PowerShell → Node.js。
- docs ワークスペースでは Markdown 編集を優先し、不要な実行系変更を避ける。
- 検証は最小単位から行い、不要なフル処理や無関係な変更を避ける。
