# CLAUDE.md

## プロジェクト概要

book000 (Tomachi) の GitHub プロフィールリポジトリ。ユーザー名と同名のため、`README.md` がプロフィールページに表示される特殊なリポジトリ。アプリケーションコードは持たず、以下を自動化する。

- プロフィール `README.md` の管理
- GitHub metrics SVG (`github-metrics.svg`) の毎時自動更新
- monthly update issue の毎月自動作成 (book000 / tomacheese / jaoafa の Renovate PR 一覧の収集処理を含む)

`package.json` 等のパッケージ定義はなく、処理はすべて GitHub Actions 上の Bash + `gh` + `jq` で実行される。

## 開発コマンド

ローカルビルド/テストは存在しない。動作確認はワークフローの手動実行で行う。

```bash
gh workflow run metrics.yml         # metrics SVG 更新を手動実行
gh workflow run monthly-update.yml  # monthly update issue 作成を手動実行
```

変更前の静的チェック:

- YAML: 構文確認 (GitHub Actions の標準構造に従う)
- Bash: `shellcheck` で構文確認

## アーキテクチャと主要ファイル

```
.
├── README.md                          # プロフィール表示 (MIT ライセンスで公開)
├── github-metrics.svg                 # metrics SVG (自動生成・手動編集禁止)
├── LICENSE                            # MIT License
└── .github/
    ├── workflows/
    │   ├── metrics.yml                # metrics SVG を毎時生成・コミット
    │   └── monthly-update.yml         # monthly update issue を毎月作成
    ├── update-template.md             # monthly update issue のテンプレート
    └── FUNDING.yml                    # GitHub Sponsors 設定
```

- **metrics.yml**: `book000/metrics@master` (lowlighter/metrics ベース) で SVG を生成。`output_action: none` で生成し後続ステップが手動コミットする (Docker イメージに git が無いため)。`github-actions[bot]` の push では再実行しない (`if` 条件で無限ループを回避)。認証は `secrets.METRICS_TOKEN`、コミット/ push は `github.token`。
- **monthly-update.yml**: 毎月 1 日に実行。次の PR 番号を計算 (既存 issue/PR 番号のギャップを探索、最大 50 回試行) し、`update-template.md` のプレースホルダーを `sed` で置換して issue を作成する。

## コーディング規約

- **会話言語**: 日本語。日本語と英数字の間には半角スペースを入れる。
- **コミット**: [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) 準拠。`<type>(<scope>): <description>`、description は日本語。例: `feat: monthly update issue の自動作成機能を追加`
- **ブランチ**: [Conventional Branch](https://conventional-branch.github.io) 短縮形。例: `feat/add-monthly-update`
- **コード内コメント**: 日本語。**エラーメッセージ**: 英語。
- **YAML**: インデントはスペース 2 個。
- **Bash**: GitHub Actions の `run` で実行するため shebang 不要。`set -e` 等のエラーハンドリングを設定。GitHub Actions の変数は `${{ }}`、Bash 変数は `$変数名` で参照。

## 変更時の注意 (リポジトリ固有)

- `github-metrics.svg` は自動生成物。手動編集しない。
- `monthly-update.yml` は `{{ date }}` / `{{ pr-number }}` / `{{ *-renovate-success-prs }}` / `{{ *-renovate-failure-prs }}` を置換する処理を持つ。ただし現状 `update-template.md` に実在するプレースホルダーは `{{ pr-number }}` のみで、他は置換処理はあるがテンプレートには含まれていない。プレースホルダーを追加/削除する場合は `monthly-update.yml` の該当処理と対で保ち、直接値を埋めない。
- Renovate PR リストは book000 / tomacheese / jaoafa の 3 オーナー分を収集する。オーナーを追加/変更する場合は monthly-update.yml の該当ブロックとテンプレートのプレースホルダーを対で修正する。
- monthly update issue では URL を `github.com` → `togithub.com` に置換している (通知抑制目的)。この置換を外さない。
- `README.md` は MIT ライセンスで公開され、他ユーザーがプロフィール作成の参考にする前提。編集時はプロフィールページでの見え方を意識する。
- Renovate が作成した PR には追加コミットしない。

## セキュリティ

- GitHub Token をハードコードしない。`secrets.METRICS_TOKEN` または `${{ github.token }}` を使う。
- トークン/シークレットをログに出力しない。
- 認証情報はリポジトリ Secrets で管理する。

## ドキュメント更新

- `README.md`: プロフィール情報を変更したとき。
- ワークフロー / `update-template.md`: 挙動を変えたとき、この CLAUDE.md と `.github/copilot-instructions.md` の該当記述も更新する。
