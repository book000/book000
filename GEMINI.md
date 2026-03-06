# Gemini CLI 作業方針

## 目的

このドキュメントは、Gemini CLI がこのプロジェクト (book000 の GitHub プロフィールリポジトリ) で作業する際のコンテキストと作業方針を定義します。

## 出力スタイル

- **言語**: 日本語で回答する
- **トーン**: 技術的で正確な情報を提供する
- **形式**: Markdown 形式で構造化された回答を提供する

## 共通ルール

- **会話言語**: 日本語
- **コミット規約**: [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) に従う
  - 形式: `<type>(<scope>): <description>`
  - `<description>` は日本語で記載
  - 例: `feat: monthly update issue の自動作成機能を追加`
- **日本語と英数字の間**: 半角スペースを挿入する

## プロジェクト概要

- **目的**: GitHub プロフィールリポジトリ。個人プロフィールの表示と、GitHub metrics の自動更新、monthly update issue の自動作成を行う。
- **主な機能**:
  - プロフィール README.md の管理
  - GitHub metrics SVG の毎時自動更新（gh-metrics/metrics（lowlighter/metrics ベース）を使用）
  - monthly update issue の自動作成（book000, tomacheese, jaoafa の Renovate PR リスト含む）

## 技術スタック

- **GitHub Actions**: ワークフローの自動実行
- **YAML**: GitHub Actions ワークフロー定義
- **Bash**: シェルスクリプト（GitHub Actions 内で使用）
- **GitHub CLI (gh)**: GitHub API の操作、PR/Issue の検索・作成
- **jq**: JSON データの処理
- **gh-metrics/metrics**: GitHub metrics SVG の生成（lowlighter/metrics ベース）

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
- エラーメッセージ: 英語

## 開発コマンド

このプロジェクトは `package.json` を使用していないため、主に GitHub CLI (`gh`) を使用して操作します。

```bash
# metrics.yml の実行
gh workflow run metrics.yml

# monthly-update.yml の実行
gh workflow run monthly-update.yml
```

## GitHub Actions ワークフロー

### metrics.yml

- **トリガー**: 毎時実行、手動実行、master/main ブランチへの push
- **処理**: gh-metrics/metrics を使用して GitHub metrics SVG を生成・更新
- **シークレット**: `METRICS_TOKEN` を使用

### monthly-update.yml

- **トリガー**: 毎月 1 日 00:00 UTC、手動実行
- **処理**:
  1. 現在の日付を取得
  2. 次の PR 番号を計算（既存の issue/PR 番号から利用可能な番号を検索）
  3. `.github/update-template.md` のプレースホルダーを置換
  4. book000, tomacheese, jaoafa の Renovate PR を検索し、成功/失敗で分類
  5. monthly update issue を作成

## 注意事項

- **認証情報**: GitHub Token をハードコーディングしない。シークレットまたは `${{ github.token }}` を使用する
- **ログへの機密情報出力**: トークンやシークレットをログに出力しない
- **既存ルールの優先**: GitHub Actions の標準的な構造に従う
- **既知の制約**:
  - github-metrics.svg は自動生成されるファイルなので、手動で編集しない
  - .github/update-template.md はプレースホルダーを含むテンプレートなので、直接編集せず、ワークフローで置換する

## リポジトリ固有

- **README.md**: MIT ライセンスで公開されており、他のユーザーがプロフィール作成の参考にできる
- **github-metrics.svg**: 自動生成されるファイルなので、手動で編集しない
- **.github/update-template.md**: monthly update issue のテンプレート。プレースホルダー（`{{ date }}`, `{{ pr-number }}`, `{{ book000-renovate-success-prs }}` など）が含まれる
- **Renovate PR リスト**: book000, tomacheese, jaoafa の 3 つのオーナーの Renovate PR を収集・表示
- **PR 番号計算**: 既存の issue/PR 番号から、転送や削除によるギャップを考慮して、次に利用可能な番号を検索。最大 50 回の試行で利用可能な番号を見つける
- **GitHub CLI**: `gh` コマンドを使用して GitHub API を操作。認証は `${{ github.token }}` または `METRICS_TOKEN` シークレットを使用
- **togithub.com**: monthly update issue では、GitHub の URL を togithub.com に置換してプライバシーを保護
- **gh-metrics/metrics**: GitHub metrics SVG の生成に使用。lowlighter/metrics ベースのため、最新の仕様や機能については公式ドキュメントを参照

## Gemini CLI の役割

Gemini CLI は、以下の観点で相談を受けることができる：

- **GitHub CLI の最新仕様や機能**: `gh` コマンドの最新の使い方や新機能
- **GitHub Actions の最新仕様や機能**: GitHub Actions の最新の機能や変更点
- **lowlighter/metrics の最新仕様や機能**: gh-metrics/metrics のベースとなる GitHub metrics SVG 生成の最新の設定や機能
- **jq の最新仕様や機能**: JSON データ処理の最新の方法
- **外部一次情報の確認**: GitHub や lowlighter/metrics の公式ドキュメントの確認
- **最新仕様の調査**: 技術スタックの最新バージョンや仕様の調査
- **外部前提条件の検証**: GitHub API の制限や制約の確認