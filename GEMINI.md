# GEMINI.md - Gemini CLI 作業方針

## 目的

このファイルは、Gemini CLI がこのリポジトリで作業する際のコンテキストと作業方針を定義します。

## 出力スタイル

- **言語**: 日本語
- **トーン**: 明確で簡潔、技術的に正確
- **形式**: Markdown 形式で構造化された出力

## 共通ルール

### 言語ルール

- **会話言語**: 日本語
- **コード内コメント**: 日本語
- **エラーメッセージ**: 英語
- **日本語と英数字の間**: 半角スペースを挿入

### コミット・PR ルール

- **コミットメッセージ**: [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) に従う
  - 形式: `<type>(<scope>): <description>`
  - `<description>` は日本語で記載
  - 例: `feat: メトリクス生成ワークフローを追加`
- **ブランチ命名**: [Conventional Branch](https://conventional-branch.github.io) に従う
  - 形式: `<type>/<description>`
  - `<type>` は短縮形（feat, fix）を使用

## プロジェクト概要

- **目的**: book000 (Tomachi) の GitHub プロフィールリポジトリを管理
- **主な機能**:
  - GitHub メトリクスの自動生成（hourly）
  - 月次更新 Issue の自動作成（monthly）
  - プロフィール README の管理
- **技術スタック**: GitHub Actions, Bash, YAML, Markdown

## コーディング規約

### フォーマット

- **YAML ファイル**: 2 スペースのインデント
- **Markdown**: 標準的な Markdown 記法に従う
- **Bash スクリプト**: ShellCheck に準拠

### 命名規則

- **ワークフローファイル**: kebab-case（例: `monthly-update.yml`）
- **ブランチ**: Conventional Branch に従う（例: `feat/add-feature`）

### コメント・エラーメッセージ

- **コメント言語**: 日本語
- **エラーメッセージ**: 英語

## 開発コマンド

このリポジトリはプロフィールリポジトリのため、通常の開発コマンドはありません。

### ワークフロー実行

```bash
# Metrics の手動実行
gh workflow run metrics.yml

# 月次更新 Issue の手動作成
gh workflow run monthly-update.yml

# ワークフローの実行状況を確認
gh run list

# 特定のワークフローの実行履歴を確認
gh run list --workflow=metrics.yml
```

### ローカルでの確認

```bash
# ワークフローの構文チェック
gh workflow list

# bash スクリプトの構文チェック（ShellCheck）
shellcheck .github/workflows/*.yml
```

## 注意事項

### セキュリティ / 機密情報

- **認証情報のコミット禁止**: API キーやトークンをコードにハードコードしない
- **ログへの機密情報出力禁止**: ログに個人情報や認証情報を出力しない
- **GitHub Secrets の使用**: トークンは GitHub Secrets に保存し、ワークフローで参照する

### 既存ルールの優先

- プロジェクト固有のルールや慣習がある場合は、それを優先する
- 既存のコードスタイルに従う

### 既知の制約

- このリポジトリはプロフィールリポジトリのため、パッケージマネージャや依存関係管理は存在しない
- GitHub Actions のみで自動化が行われている

## リポジトリ固有

### プロジェクトの特徴

- このリポジトリは GitHub プロフィールページ（`https://github.com/book000`）として表示される
- README.md の変更は即座にプロフィールページに反映される
- MIT ライセンスで公開されており、他者がプロフィール README の参考として利用可能

### ワークフロー

1. **metrics.yml**
   - GitHub メトリクスの SVG を hourly で生成
   - `gh-metrics/metrics@master` アクションを使用
   - 生成された SVG は `github-metrics.svg` として保存

2. **monthly-update.yml**
   - 月初に Renovate PR の一覧を含む Issue を作成
   - `.github/update-template.md` をテンプレートとして使用
   - book000, tomacheese, jaoafa の各組織の Renovate PR を集計

### 関連プロジェクト

- `github-webhook-bridge` ディレクトリには、別プロジェクト（[book000/github-webhook-bridge](https://github.com/book000/github-webhook-bridge)）の設定ファイルが含まれる

### Gemini CLI の役割

Gemini CLI は以下の用途で使用されることを想定しています：

- GitHub Actions の最新仕様や機能に関する情報提供
- `gh` CLI の最新機能や使い方の確認
- 外部サービス（Metrics、Renovate など）の最新情報の調査
- 最新のベストプラクティスの提案
