# Copilot code review instructions

book000 (Tomachi) の GitHub プロフィールリポジトリ。`README.md` がプロフィールページに表示される。アプリケーションコードはなく、変更対象はほぼ GitHub Actions ワークフロー (Bash + `gh` + `jq`)、`README.md`、`.github/update-template.md`。

## 規約 (レビューで確認する点)

- コミットメッセージは Conventional Commits (`<type>(<scope>): <description>`、description は日本語)。
- 日本語と英数字の間には半角スペースを入れる。コード内コメントは日本語、エラーメッセージは英語。
- YAML はインデント 2 スペース。
- Bash: エラーハンドリング (`set -e` 等) が設定されているか確認する。GitHub Actions 変数は `${{ }}`、Bash 変数は `$名前` で参照する。

## 重点的に指摘すべき点

- **トークン漏洩**: GitHub Token のハードコード、トークン/シークレットのログ出力を必ず指摘する。認証は `secrets.METRICS_TOKEN` または `${{ github.token }}` を使う。
- **`gh` / `jq` パイプラインの失敗**: 失敗しうる箇所でエラーが握り潰されていないか (意図しない空出力での issue 作成など) を確認する。
- **プレースホルダーの対応漏れ**: `monthly-update.yml` は `{{ date }}` / `{{ pr-number }}` / `{{ *-renovate-success-prs }}` / `{{ *-renovate-failure-prs }}` の置換処理を持つ (現状 `update-template.md` に実在するのは `{{ pr-number }}` のみ)。プレースホルダーを追加/変更した場合、テンプレートと `monthly-update.yml` の置換処理の対応が取れているか確認する。

## フラグしないでよい既知パターン (誤検知しやすい)

- `github-metrics.svg` は `book000/metrics` による自動生成物。差分が大きくても手書きコードとしてレビューしない。
- `update-template.md` 内の `{{ ... }}` はワークフローが置換するプレースホルダーであり、未定義変数やテンプレート構文エラーではない。
- URL の `github.com` → `togithub.com` 置換は通知抑制のための意図的な処理。バグとして指摘しない。
- metrics コミットの `[Skip GitHub Action]` 表記、および `github-actions[bot]` の push をスキップする `if` 条件は、再実行ループ回避のための意図的な設計。
- `jq ... 2>/dev/null` は出力が空になりうるケースを許容する意図的な記述 (`|| true` と併用)。単純なエラー無視として指摘しない。
