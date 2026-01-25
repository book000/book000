# GitHub Copilot Instructions

## プロジェクト概要

- **目的**: book000 (Tomachi) の GitHub プロフィールリポジトリを管理
- **主な機能**:
  - GitHub メトリクスの自動生成と更新（hourly）
  - 月次更新 Issue の自動作成（monthly）
  - プロフィール README の管理
- **対象ユーザー**: book000 本人および協力者

## 共通ルール

- 会話は日本語で行う。
- PR とコミットは Conventional Commits に従う。`<description>` は日本語で記載する。
  - 例: `feat: メトリクス生成ワークフローを追加`
- 日本語と英数字の間には半角スペースを入れる。

## 技術スタック

- **言語**: Markdown, Bash, YAML
- **GitHub Actions**: ワークフローの自動実行
- **使用ツール**:
  - `gh` CLI（GitHub CLI）
  - `jq`（JSON 処理）
  - `sed`（テキスト処理）
- **パッケージマネージャー**: なし（プロフィールリポジトリのため）

## コーディング規約

- **コメント言語**: 日本語
- **エラーメッセージ**: 英語
- **YAML ファイル**: 2 スペースのインデント
- **Bash スクリプト**: ShellCheck に準拠

## 開発コマンド

このリポジトリはプロフィールリポジトリのため、通常の開発コマンドはありません。

### ワークフロー実行

```bash
# Metrics の手動実行
gh workflow run metrics.yml

# 月次更新 Issue の手動作成
gh workflow run monthly-update.yml
```

### ローカルでのワークフロー確認

```bash
# ワークフローの構文チェック
gh workflow list

# 最新のワークフロー実行状況を確認
gh run list
```

## テスト方針

- **テストフレームワーク**: なし
- **手動テスト**: ワークフローの手動実行により動作を確認

## セキュリティ / 機密情報

- GitHub Secrets に保存された `METRICS_TOKEN` を使用する。
- トークンやシークレットをコードやログに出力しない。
- プライベートリポジトリの情報を公開しない。

## ドキュメント更新

以下のドキュメントを適宜更新する必要があります：

- **README.md**: プロフィール情報、スキル、リンクを最新に保つ
- **.github/update-template.md**: 月次更新 Issue のテンプレート
- ワークフローファイル: 変更時は動作確認を実施

## リポジトリ固有

- このリポジトリは GitHub プロフィールページ（`https://github.com/book000`）として表示される。
- README.md の変更は即座にプロフィールページに反映される。
- GitHub Actions ワークフローは以下の2つ：
  - `metrics.yml`: GitHub メトリクスの SVG を hourly で生成
  - `monthly-update.yml`: 月初に Renovate PR の一覧を含む Issue を作成
- `github-webhook-bridge` ディレクトリには、別プロジェクトの設定ファイルが含まれる。
- MIT ライセンスで公開されており、他者がプロフィール README の参考として利用可能。
