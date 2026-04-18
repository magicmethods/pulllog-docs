# PullLog 運用ガイド

この文書は PullLog の運用と保守に関する公開向け概要です。  
サービス監視、デプロイ、インシデント対応、バックアップ方針を高水準で説明します。

---

## 公開運用概要

- PullLog は frontend、backend、database を分離した責務で運用します
- リリース、監視、バックアップ、インシデント対応の詳細手順は backend subproject 側で管理します
- 障害やメンテナンスの公開告知は適切な公開チャネルで行います

この公開文書では、ブランチ戦略、保持期間、ヘルスチェック設計、鍵ローテーション詳細を正本方針として再掲しません。

## 正本参照

- Backend のサービス運用概要: `backend/docs/operations/service-operations-overview.md`
- Backend のデプロイとロールバック手順: `backend/docs/operations/deploy-and-release.md`
- Frontend のビルドとデプロイ手順: `frontend/docs/operations/deploy-and-build.md`
- 公開セキュリティ報告方針: `../SECURITY.md`

## 公開方針

- サービス通信は HTTPS で保護されます
- デプロイとロールバックは各 subproject 所有の手順で管理します
- 監視、バックアップ、セキュリティ運用は implementation-owned な backend 文書で管理します

## インシデント告知

- 障害やメンテナンスの公開告知は公式チャネルから行う場合があります
- セキュリティ開示は [SECURITY.md](../SECURITY.md) に従ってください

---

最終更新: 2025年8月