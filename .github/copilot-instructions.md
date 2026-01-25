# GitHub Copilot Instructions

## プロジェクト概要

- **目的**: GitHub プロフィールリポジトリ。個人プロフィールの表示と、GitHub metrics の自動更新、monthly update issue の自動作成を行う。
- **主な機能**:
  - プロフィール README.md の管理
  - GitHub metrics SVG の毎時自動更新
  - monthly update issue の自動作成（book000, tomacheese, jaoafa の Renovate PR リスト含む）
- **対象ユーザー**: book000 (Tomachi) 本人

## 共通ルール

- **会話言語**: 日本語
- **コミット規約**: [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) に従う
  - 形式: `<type>(<scope>): <description>`
  - `<description>` は日本語で記載
  - 例: `feat: monthly update issue の自動作成機能を追加`
- **ブランチ命名**: [Conventional Branch](https://conventional-branch.github.io) に従う
  - 形式: `<type>/<description>`
  - `<type>` は短縮形（feat, fix）を使用
  - 例: `feat/add-monthly-update`
- **日本語と英数字の間**: 半角スペースを挿入する

## 技術スタック

- **GitHub Actions**: ワークフローの自動実行
- **YAML**: GitHub Actions ワークフロー定義
- **Bash**: シェルスクリプト（GitHub Actions 内で使用）
- **GitHub CLI (gh)**: GitHub API の操作、PR/Issue の検索・作成
- **jq**: JSON データの処理

## コーディング規約

### YAML

- GitHub Actions の標準的な構造に従う
- インデント: スペース 2 個
- コメント: 日本語で記述

### Bash

- Shebang: 不要（GitHub Actions の run で実行）
- `set -e` などのエラーハンドリングは適切に設定
- 変数参照: `${{ }}` 形式（GitHub Actions の変数）、`$変数名` 形式（Bash の変数）
- コメント: 日本語で記述

## 開発コマンド

このプロジェクトは `package.json` を使用していないため、主に GitHub CLI (`gh`) を使用して操作します。

```bash
# metrics.yml の実行
gh workflow run metrics.yml

# monthly-update.yml の実行
gh workflow run monthly-update.yml
```

## テスト方針

- **テストフレームワーク**: なし（GitHub Actions のワークフローのみ）
- **テスト方法**: GitHub Actions のワークフローを手動実行して動作確認

## セキュリティ / 機密情報

- **GitHub Token**: `METRICS_TOKEN` シークレットと `${{ github.token }}` を使用
- **認証情報**: GitHub リポジトリの Secrets で管理
- **ログ**: トークンやシークレットをログに出力しない

## ドキュメント更新

以下の変更があった場合、関連ドキュメントを更新する：

- **README.md**: プロフィール情報の変更時
- **GitHub Actions ワークフロー**: ワークフロー変更時、このファイルとプロンプトファイルを更新

## リポジトリ固有

- **README.md**: MIT ライセンスで公開されており、他のユーザーがプロフィール作成の参考にできる
- **github-metrics.svg**: 自動生成されるファイルなので、手動で編集しない
- **.github/update-template.md**: monthly update issue のテンプレート。プレースホルダー（`{{ date }}`, `{{ pr-number }}` など）が含まれる
- **Renovate PR リスト**: book000, tomacheese, jaoafa の 3 つのオーナーの Renovate PR を収集・表示
- **PR 番号計算**: 既存の issue/PR 番号から、転送や削除によるギャップを考慮して、次に利用可能な番号を検索