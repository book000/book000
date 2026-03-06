# AI エージェント作業方針

## 目的

このドキュメントは、一般的な AI エージェントがこのプロジェクト (book000 の GitHub プロフィールリポジトリ) で作業する際の基本方針を定義します。

## 基本方針

- **会話言語**: 日本語
- **コード内コメント**: 日本語
- **エラーメッセージ**: 英語
- **コミット規約**: [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) に従う
  - 形式: `<type>(<scope>): <description>`
  - `<description>` は日本語で記載
  - 例: `feat: monthly update issue の自動作成機能を追加`

## プロジェクト概要

- **目的**: GitHub プロフィールリポジトリ。個人プロフィールの表示と、GitHub metrics の自動更新、monthly update issue の自動作成を行う。
- **主な機能**:
  - プロフィール README.md の管理
  - GitHub metrics SVG の毎時自動更新（gh-metrics/metrics（lowlighter/metrics ベース）を使用）
  - monthly update issue の自動作成（book000, tomacheese, jaoafa の Renovate PR リスト含む）

## 判断記録のルール

すべての判断は、以下の形式で記録すること：

1. **判断内容の要約**: 何を決定したか
2. **検討した代替案**: どのような選択肢があったか
3. **採用しなかった案とその理由**: なぜその選択肢を選ばなかったか
4. **前提条件・仮定・不確実性**: 判断の基盤となる前提、仮定、不確実な要素

前提・仮定・不確実性を明示し、仮定を事実のように扱わないこと。

## 技術スタック

- **GitHub Actions**: ワークフローの自動実行
- **YAML**: GitHub Actions ワークフロー定義
- **Bash**: シェルスクリプト（GitHub Actions 内で使用）
- **GitHub CLI (gh)**: GitHub API の操作、PR/Issue の検索・作成
- **jq**: JSON データの処理

## 開発手順（概要）

1. **プロジェクト理解**
   - README.md を読み、プロフィール内容を理解する
   - .github/workflows/ 配下のワークフローを確認する

2. **変更実装**
   - README.md を編集する場合: プロフィール情報を更新
   - GitHub Actions ワークフローを編集する場合: YAML ファイルを更新
   - .github/update-template.md を編集する場合: テンプレートを更新

3. **動作確認**
   - YAML 構文エラーがないことを確認（YAML linter）
   - Bash スクリプトの構文エラーがないことを確認（shellcheck）
   - GitHub Actions のワークフローを手動実行して動作確認
     - 例: `gh workflow run metrics.yml`

## セキュリティ / 機密情報

- **GitHub Token**: `METRICS_TOKEN` シークレットと `${{ github.token }}` を使用。トークンをハードコーディングしない
- **認証情報**: GitHub リポジトリの Secrets で管理
- **ログ**: トークンやシークレットをログに出力しない

## リポジトリ固有

- **README.md**: MIT ライセンスで公開されており、他のユーザーがプロフィール作成の参考にできる
- **github-metrics.svg**: 自動生成されるファイルなので、手動で編集しない
- **.github/update-template.md**: monthly update issue のテンプレート。プレースホルダー（`{{ date }}`, `{{ pr-number }}`, `{{ book000-renovate-success-prs }}` など）が含まれる
- **Renovate PR リスト**: book000, tomacheese, jaoafa の 3 つのオーナーの Renovate PR を収集・表示
- **PR 番号計算**: 既存の issue/PR 番号から、転送や削除によるギャップを考慮して、次に利用可能な番号を検索
- **togithub.com**: monthly update issue では、GitHub の URL を togithub.com に置換してプライバシーを保護