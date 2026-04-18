# PullLog 用語集

この文書は、PullLog 各リポジトリで使う workspace と subproject の用語に関する正本です。

## 標準用語

- Workspace: frontend、backend、contract、pulllog-docs など複数のトップレベルディレクトリで構成される PullLog 全体の開発単位
- Subproject: PullLog workspace に参加する各トップレベルディレクトリ

## 使用方針

- PullLog の日常的な文書や開発上の会話では、workspace を PullLog 全体の開発単位として使います
- subproject は workspace 内の各トップレベルディレクトリを指す用語として使います
- README、agent guidance、設計メモを含め、この用語を一貫して使います

## 例外

- Visual Studio Code の機能や設定に言及する場合は、必要に応じて公式用語である workspace と workspace folder を使います
- pnpm の挙動や設定に言及する場合は、公式用語である pnpm workspace を使います
- 外部ツール、コマンド、外部文書を引用する場合は、PullLog 内部用語と異なっていても原文の用語を保持します

## 適用範囲

この用語方針は PullLog のリポジトリ運用と文書作成を対象とします。外部ツールの公式用語を置き換えるものではありません。