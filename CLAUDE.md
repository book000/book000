# Claude Code 作業方針

## 目的

このドキュメントは、Claude Code がこのプロジェクト (book000 の GitHub プロフィールリポジトリ) で作業する際の方針とプロジェクト固有のルールを定義します。

## 判断記録のルール

すべての判断は、以下の形式で記録すること：

1. **判断内容の要約**: 何を決定したか
2. **検討した代替案**: どのような選択肢があったか
3. **採用しなかった案とその理由**: なぜその選択肢を選ばなかったか
4. **前提条件・仮定・不確実性**: 判断の基盤となる前提、仮定、不確実な要素
5. **他エージェントによるレビュー可否**: 他のエージェント（Codex CLI、Gemini CLI）によるレビューが必要か

前提・仮定・不確実性を明示し、仮定を事実のように扱わないこと。

## プロジェクト概要

- **目的**: GitHub プロフィールリポジトリ。個人プロフィールの表示と、GitHub metrics の自動更新、monthly update issue の自動作成を行う。
- **主な機能**:
  - プロフィール README.md の管理
  - GitHub metrics SVG の毎時自動更新（lowlighter/metrics を使用）
  - monthly update issue の自動作成（book000, tomacheese, jaoafa の Renovate PR リスト含む）

## 重要ルール

- **会話言語**: 日本語
- **コミット規約**: [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) に従う
  - 形式: `<type>(<scope>): <description>`
  - `<description>` は日本語で記載
  - 例: `feat: monthly update issue の自動作成機能を追加`
- **コード内コメント**: 日本語
- **エラーメッセージ**: 英語

## 環境のルール

- **ブランチ命名**: [Conventional Branch](https://conventional-branch.github.io) に従う
  - 形式: `<type>/<description>`
  - `<type>` は短縮形（feat, fix）を使用
  - 例: `feat/add-monthly-update`
- **GitHub リポジトリ調査**: テンポラリディレクトリに git clone して調査する
- **実行環境**: GitHub Actions（ubuntu-latest）
- **Renovate PR**: Renovate が作成した既存の PR に対して追加コミットや更新を行わない

## コード改修時のルール

- **日本語と英数字の間**: 半角スペースを挿入する
- **既存のエラーメッセージ**: 先頭に絵文字がある場合は、全体で統一する

### YAML 規約

- GitHub Actions の標準的な構造に従う
- インデント: スペース 2 個
- コメント: 日本語で記述

### Bash 規約

- Shebang: 不要（GitHub Actions の run で実行）
- `set -e` などのエラーハンドリングは適切に設定
- 変数参照: `${{ }}` 形式（GitHub Actions の変数）、`$変数名` 形式（Bash の変数）
- コメント: 日本語で記述

## 相談ルール

他エージェントに相談することができる。以下の観点で使い分ける：

### Codex CLI (ask-codex)

- GitHub Actions ワークフローのコードレビュー
- Bash スクリプトの実装方針や改善提案
- YAML 構造の整合性確認
- セキュリティ上の問題（トークン漏洩など）の検出

### Gemini CLI (ask-gemini)

- GitHub CLI (gh) の最新仕様や機能
- GitHub Actions の最新仕様や機能
- lowlighter/metrics の最新仕様や機能
- 外部一次情報の確認、最新仕様の調査、外部前提条件の検証

### 指摘への対応

他エージェントが指摘・異議を提示した場合、以下のいずれかを行う。黙殺・無言での不採用は禁止する。

- 指摘を受け入れ、判断を修正する
- 指摘を退け、その理由を明示する

以下は必ず実施する：

- 他エージェントの提案を鵜呑みにせず、その根拠や理由を理解する
- 自身の分析結果と他エージェントの意見が異なる場合は、双方の視点を比較検討する
- 最終的な判断は、両者の意見を総合的に評価した上で、自身で下す

## GitHub Actions ワークフロー

### metrics.yml

```yaml
# GitHub metrics SVG の自動更新
トリガー: 毎時実行、手動実行、master/main ブランチへの push
処理: gh-metrics/metrics を使用して GitHub metrics SVG を生成・更新
シークレット: METRICS_TOKEN
```

### monthly-update.yml

```yaml
# monthly update issue の自動作成
トリガー: 毎月 1 日 00:00 UTC、手動実行
処理:
  1. 現在の日付を取得
  2. 次の PR 番号を計算（既存の issue/PR 番号から利用可能な番号を検索）
  3. .github/update-template.md のプレースホルダーを置換
  4. book000, tomacheese, jaoafa の Renovate PR を検索し、成功/失敗で分類
  5. monthly update issue を作成
```

## アーキテクチャと主要ファイル

### アーキテクチャサマリー

このプロジェクトは、以下のコンポーネントで構成される：

1. **README.md**: プロフィール表示
   - 個人情報、スキル、リンク、連絡先など

2. **github-metrics.svg**: GitHub metrics SVG
   - lowlighter/metrics で自動生成

3. **.github/workflows/metrics.yml**: metrics 自動更新ワークフロー
   - 毎時実行して github-metrics.svg を更新

4. **.github/workflows/monthly-update.yml**: monthly update issue 自動作成ワークフロー
   - 毎月 1 日に実行して、Renovate PR リストを含む issue を作成

5. **.github/update-template.md**: monthly update issue テンプレート
   - プレースホルダー（`{{ date }}`, `{{ pr-number }}` など）を含む

### 主要ディレクトリ

```
.
├── README.md                           # プロフィール表示
├── github-metrics.svg                  # GitHub metrics SVG（自動生成）
├── .github/
│   ├── workflows/
│   │   ├── metrics.yml                 # metrics 自動更新ワークフロー
│   │   └── monthly-update.yml          # monthly update issue 自動作成ワークフロー
│   ├── update-template.md              # monthly update issue テンプレート
│   └── FUNDING.yml                     # GitHub Sponsors 設定
└── LICENSE                             # MIT License
```

## 実装パターン

### 推奨パターン

#### PR 番号計算

```bash
# 既存の issue/PR 番号から、転送や削除によるギャップを考慮して、次に利用可能な番号を検索
ISSUE_NUMBERS=$(gh api --paginate /repos/book000/book000/issues?state=all | jq -r '.[].number' 2>/dev/null | sort -n || true)
PR_NUMBERS=$(gh api --paginate /repos/book000/book000/pulls?state=all | jq -r '.[].number' 2>/dev/null | sort -n || true)
ALL_NUMBERS=$(echo -e "$ISSUE_NUMBERS\n$PR_NUMBERS" | grep -E '^[0-9]+$' | sort -n | uniq)

# ギャップを検索し、利用可能な番号を見つける
```

#### Renovate PR リスト取得

```bash
# 成功した Renovate PR を取得
gh search prs archived:false --owner book000 --state open --app renovate --sort created --order desc --checks success --json repository,number,title,url | jq -r '.[] | ["- [ ] [" + .title + " - " + .repository.nameWithOwner + "#" + (.number|tostring) + "](" + .url|sub("github.com";"togithub.com") + ")"] | add'

# 失敗した Renovate PR を取得
gh search prs archived:false --owner book000 --state open --app renovate --sort created --order desc --checks failure --json repository,number,title,url | jq -r '.[] | ["- [ ] [" + .title + " - " + .repository.nameWithOwner + "#" + (.number|tostring) + "](" + .url|sub("github.com";"togithub.com") + ")"] | add'
```

#### テンプレートのプレースホルダー置換

```bash
# sed でプレースホルダーを置換
sed -i -e "s/{{ date }}/$DATE/g" .github/update-template.md
sed -i -e "s/{{ pr-number }}/$PR_NUMBER/g" .github/update-template.md

# sed でファイルの内容を挿入
sed -i -e "/{{ book000-renovate-success-prs }}/r book000-success-prs.txt" -e "/{{ book000-renovate-success-prs }}/d" .github/update-template.md
```

### 非推奨パターン

- **GitHub Token のハードコーディング**: シークレットまたは `${{ github.token }}` を使用する
- **エラーハンドリングの省略**: GitHub CLI コマンドが失敗する可能性がある場合は適切にハンドリングする
- **jq のエラー無視**: `2>/dev/null` で jq のエラーを無視する場合は、適切な理由があることを確認する

## テスト

### テスト方針

- **ワークフローのテスト**: GitHub Actions のワークフローを手動実行（workflow_dispatch）して動作確認
- **PR 番号計算のテスト**: ローカル環境で Bash スクリプトを実行して、正しい番号が計算されることを確認
- **Renovate PR リスト取得のテスト**: ローカル環境で GitHub CLI コマンドを実行して、正しい PR リストが取得されることを確認

### 追加テスト条件

変更を加えた場合、以下を確認する：

1. YAML 構文エラーがないこと（YAML linter で確認）
2. Bash スクリプトの構文エラーがないこと（shellcheck で確認）
3. GitHub CLI コマンドが正しく動作すること
4. jq コマンドが正しく動作すること
5. プレースホルダーが正しく置換されること

## ドキュメント更新ルール

### 更新対象

以下のファイルを変更した場合は、関連ドキュメントを更新する：

- **README.md**: プロフィール情報の変更時
- **GitHub Actions ワークフロー**: ワークフロー変更時、プロンプトファイルを更新
- **.github/update-template.md**: テンプレート変更時、プロンプトファイルを更新

### 更新タイミング

- GitHub Actions ワークフローの変更時
- 新しい機能の追加時
- プロジェクト要件の変更時
- 品質チェックで問題検出時

## 作業チェックリスト

### 新規改修時

1. プロジェクトを理解する
2. 作業ブランチが適切であることを確認する
3. 最新のリモートブランチに基づいた新規ブランチであることを確認する
4. PR がクローズされた不要ブランチが削除済みであることを確認する

### コミット・プッシュ前

1. Conventional Commits に従っていることを確認する
2. センシティブな情報（トークンなど）が含まれていないことを確認する
3. YAML 構文エラーがないことを確認する
4. Bash スクリプトの構文エラーがないことを確認する（shellcheck）

### PR 作成前

1. PR 作成の依頼があることを確認する
2. センシティブな情報が含まれていないことを確認する
3. コンフリクトの恐れがないことを確認する

### PR 作成後

1. コンフリクトがないことを確認する
2. PR 本文が最新状態のみを網羅していることを確認する
3. `gh pr checks <PR ID> --watch` で CI を確認する
4. Copilot レビューに対応し、コメントに返信する
5. Codex のコードレビューを実施し、信頼度スコアが 50 以上の指摘対応を行う
6. PR 本文の崩れがないことを確認する

## リポジトリ固有

- **README.md**: MIT ライセンスで公開されており、他のユーザーがプロフィール作成の参考にできる
- **github-metrics.svg**: 自動生成されるファイルなので、手動で編集しない
- **.github/update-template.md**: monthly update issue のテンプレート。プレースホルダー（`{{ date }}`, `{{ pr-number }}`, `{{ book000-renovate-success-prs }}` など）が含まれる
- **Renovate PR リスト**: book000, tomacheese, jaoafa の 3 つのオーナーの Renovate PR を収集・表示
- **PR 番号計算**: 既存の issue/PR 番号から、転送や削除によるギャップを考慮して、次に利用可能な番号を検索。最大 50 回の試行で利用可能な番号を見つける
- **GitHub CLI**: `gh` コマンドを使用して GitHub API を操作。認証は `${{ github.token }}` または `METRICS_TOKEN` シークレットを使用
- **togithub.com**: monthly update issue では、GitHub の URL を togithub.com に置換してプライバシーを保護
