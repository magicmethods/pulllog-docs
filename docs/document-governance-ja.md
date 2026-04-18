# 文書ガバナンス

この文書は、`pulllog-docs/` subproject を中心とした PullLog の文書ガバナンスモデルを定義します。

## 目的

`pulllog-docs/` は、PullLog 全体の文書方針、用語、公開ドキュメントレビューのためのガバナンス拠点です。

ただし、これによって `pulllog-docs/` があらゆる技術詳細の正本になるわけではありません。各 subproject は、それぞれの実装固有のドキュメントについて引き続き責任を持ちます。

## ガバナンスモデル

- `pulllog-docs/` は、共有用語、公開ドキュメント方針、subproject 横断の文書監査ワークフローを管理します。
- `frontend/`、`backend/`、`contract/` は、それぞれの実装詳細、ビルド手順、技術的な正本文書を管理します。
- subproject をまたぐ修正は、小さくレビューしやすい差分と、明示的な正本参照を優先します。

## エージェント構成

### `docs-maintenance-orchestrator`
- PullLog 全体の文書監査と保守計画の入口です。
- 専門エージェントへレビューを委譲し、承認可能な計画に統合します。
- ユーザーが明示的に編集を求めない限り、計画段階で止まります。
- 自分では編集せず、承認済みの変更は `docs-maintainer` に委譲します。

### `docs-governance-auditor`
- 用語統一、正本参照の利用状況、README と AGENTS のドリフト、文書索引の鮮度を確認します。
- 文書ファイル名の一貫性も確認し、特にスネークケースとケバブケースの混在が整理対象かを判定します。
- `frontend/`、`backend/`、`contract/`、`pulllog-docs/` を対象にします。

### `public-docs-sanitizer`
- `pulllog-docs/` に対して、公開リスクのある内容、内部実装情報の漏えい、公開ナビゲーションの問題を確認します。

### `docs-maintainer`
- orchestrator で承認された文書修正を、最小差分で適用します。
- 監査結果を `.github/audit-reports/` に保存し、後から追跡できる状態を保ちます。
- `CHANGELOG.md` と `ROADMAP.md` について、明示的な依頼があり、根拠情報が確認できる場合に保守更新を行います。

### `docs-changelog-planner`
- 根拠の確認できる `CHANGELOG.md` 更新指示を準備します。
- `read` と `search` だけを使います。
- 自分では編集せず、プロジェクト記録の編集は `docs-maintainer` だけが行います。

### `docs-roadmap-planner`
- 確定済みの `ROADMAP.md` 更新指示を準備します。
- `read` と `search` だけを使います。
- 自分では編集せず、プロジェクト記録の編集は `docs-maintainer` だけが行います。

## 運用フロー

1. 複数 subproject にまたがる依頼や保守計画が必要な場合は、`docs-maintenance-orchestrator` から開始します。
2. 用語、README、AGENTS、索引、正本参照の確認には `docs-governance-auditor` を使います。
3. `pulllog-docs/` の公開コンテンツを含む場合は `public-docs-sanitizer` を使います。
4. 結果は次の区分で整理します。
   - 安全に保守できる候補
   - 人手レビューが必要な項目
   - 他 subproject が責任を持つ範囲外の項目
5. 結果を後から見返す必要がある場合は、`.github/audit-reports/README.md` で定義した yaml フロントマター形式の標準メタデータ付きで監査証跡を `.github/audit-reports/` に保存します。
   最低限、安定した `record-id`、制御された `status`、`source-records` と `target-files` の YAML 配列を含めます。
6. 編集は、ユーザーの明示的な承認または明示的な編集依頼がある場合にのみ実施し、実行は `docs-maintainer` に委譲します。

## 保守モード

### 監査是正モード
- `docs-maintenance-orchestrator` から開始します。
- 専門監査エージェントで指摘を集めます。
- 承認された指摘セットを証跡として保存します。
- 承認済みの編集だけを `docs-maintainer` に渡して実行します。

### プロジェクト記録保守モード
- 文書監査の有無に関係なく、`CHANGELOG.md` や `ROADMAP.md` のような共有記録を更新したい場合に使います。
- 優先順位付けや範囲確認が必要なら `docs-maintenance-orchestrator` から開始します。
- `CHANGELOG.md` の更新指示整理には `docs-changelog-planner` を使います。
- `ROADMAP.md` の更新指示整理には `docs-roadmap-planner` を使います。
- 更新根拠と対象ファイルが明確な場合だけ、`docs-maintainer` を直接使います。
- プロジェクト記録を実際に編集するエージェントは `docs-maintainer` だけです。
- ROADMAP には将来計画だけを、CHANGELOG には完了済みで根拠のある変更だけを記録します。

## プロンプト例

### orchestrator を入口にする場合
workspace 横断の通常監査は、原則として `docs-maintenance-orchestrator` に依頼します。

プロンプト例:
- `PullLog workspace 全体の文書監査を開始してください。今回は監査のみで、編集はしないでください。`
- `README と AGENTS に限定して文書監査を開始してください。ファイル名規約の揺れも確認してください。`
- `public docs only の範囲で監査を開始してください。公開リスクの確認を優先してください。`
- `文書監査の結果を整理し、承認後に maintainer へ渡す編集指示まで作ってください。`

### governance auditor を直接使う場合
orchestrator を介さず、特定の観点だけを確認したいときに `docs-governance-auditor` を直接使います。

プロンプト例:
- `workspace / subproject 用語の統一状況と正本参照の抜けを監査してください。編集はまだ不要です。`
- `docs 配下のファイル名がスネークケースとケバブケースで混在していないか確認してください。`
- `README、AGENTS、docs の索引にドリフトがないか確認してください。`

### public docs sanitizer を直接使う場合
`pulllog-docs/` の公開安全性だけを見たいときは `public-docs-sanitizer` を直接使います。

プロンプト例:
- `pulllog-docs の公開文書に内部情報や公開不適切な表現がないか確認してください。`
- `README と docs の公開向けナビゲーションに古いリンクがないか確認してください。`
- `public docs が他 subproject の技術正本を不適切に上書きしていないか確認してください。`

### 承認済み保守の実行
編集対象が確定していて、証跡保存も含めて実行したい場合は `docs-maintainer` を使います。

プロンプト例:
- `承認済みの README と document-governance の修正を適用し、証跡も残してください。`
- `監査結果に基づいて CHANGELOG.md と ROADMAP.md を更新してください。根拠のある内容だけ反映してください。`

### プロジェクト記録の計画
編集前に更新指示を固めたい場合は、planner エージェントを使います。

プロンプト例:
- `CHANGELOG.md に載せるべき完了済み変更を監査証跡から整理してください。編集はまだしないでください。`
- `ROADMAP.md に反映できる確定事項だけを整理し、maintainer 向け指示にしてください。`

## 運用用プロンプトテンプレート

### CHANGELOG 計画テンプレート
```text
CHANGELOG 更新指示を、ファイル編集なしで整理してください。
対象は pulllog-docs のみです。
入力:
- CHANGELOG.md
- .github/audit-reports/ 配下の承認済み証跡
要件:
- 完了済みで根拠のある項目だけを対象にする
- ROADMAP 上の意図、未決事項、保留中の follow-up は除外する
- maintainer がそのまま使える指示だけを返す
```

### ROADMAP 計画テンプレート
```text
ROADMAP 更新指示を、ファイル編集なしで整理してください。
対象は pulllog-docs のみです。
入力:
- ROADMAP.md
- .github/audit-reports/ 配下の承認済み証跡
要件:
- 公開可能で確定済みの将来項目だけを対象にする
- 完了済み変更、内部ワークフローメモ、推測段階の案は除外する
- maintainer がそのまま使える指示だけを返す
```

### プロジェクト記録更新テンプレート
```text
承認済みのプロジェクト記録保守を pulllog-docs 内だけで適用してください。
対象:
- 指定した監査証跡に保存された承認済み指示だけを反映する
要件:
- 承認済みの対象ファイルだけを編集する
- source-of-truth の境界を維持する
- .github/audit-reports/ に実行証跡を作成または更新する
- 変更ファイルに対して最小限の検証を行う
```

## 運用上の基本認識

通常の workspace 横断監査であれば、`docs-maintenance-orchestrator` に文書監査開始を依頼すれば十分です。orchestrator が必要な専門エージェントを選び、結果を集約して報告する想定です。自分で観点を絞りたい場合だけ、専門エージェントを直接呼び分けます。

編集が承認された後は、orchestrator 自身が編集するのではなく、`docs-maintainer` に作業を引き渡します。これにより、監査、承認、実行、証跡保存を分離できます。

## 正本ルール

- workspace 用語: `docs/workspace-terminology.md`
- 公開ドキュメント方針: この文書と `AGENTS.md`
- frontend 技術実装: `../frontend/`
- backend 技術実装: `../backend/`
- API 契約: `../contract/api-schema.yaml`

## 境界

- backend、frontend、contract の振る舞いを、根拠なしに public docs 側で再定義しない。
- 秘密情報、内部エンドポイント、認証情報、非公開運用情報を public docs に載せない。
- 文書整理を理由に、無関係な技術内容まで書き換えない。
- ROADMAP 上の検討事項を CHANGELOG の実績として扱わず、監査で見つけた疑義を承認済み修正指示として扱わない。

## 推奨される使い方

- workspace 全体のレビューには orchestrator を使う。
- 集中的なドリフト確認には governance auditor を直接使う。
- 公開前確認には sanitizer を直接使う。
- プロジェクト記録の更新指示整理には changelog planner と roadmap planner を使う。
- 承認済みの修正実行、証跡保存、根拠付きの CHANGELOG / ROADMAP 更新には maintainer を使う。