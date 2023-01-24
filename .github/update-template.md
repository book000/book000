## ストレージ確認

`df -h` などを活用し、ストレージの使用率を確認

- ICHIGO
  - [ ] `C`
  - [ ] `N`
- TomaPi
  - [ ] `/`
  - [ ] `/mnt/hdd`
  - [ ] `/mnt/hdd`
- Nuts
  - [ ] `/`
  - [ ] `/mnt/hdd`
- Comet
  - [ ] `/`
- jaoMain
  - [ ] `/`
- jaoWeb
  - [ ] `/`
- ZakuroHat
  - [ ] `/`
  - [ ] `/home`

## アップデート

各アプリケーション等のアップデート実施

- [ ] Computer
- [ ] Scoop
- [ ] winget
- [ ] MyMaid4

### Computer

適宜 Windows Update などを適用

### Scoop

```shell
scoop update # Scoopのリポジトリを更新
scoop status | tee scoop-{{ date }}.log # アップデート可能なアプリケーション一覧を表示
scoop update * # すべてのアプリケーションを更新
scoop status # アップデート後の一覧を確認
```

`scoop-{{ date }}.log` をこの issue のコメント欄に投稿しておくこと

### winget

```shell
winget upgrade | tee winget-{{ date }}.log # アップデート可能なアプリケーション一覧を表示
winget upgrade [...] # アップデートしたいアプリケーションをアップデート
```

`winget-{{ date }}.log` をこの issue のコメント欄に投稿しておくこと

### MyMaid4

ワークフローが生成するプルリクエストを用いて一括アップデート

[`is:pr is:open Update dependencies packages by renovate` in `jaoafa/MyMaid4`](https://github.com/jaoafa/MyMaid4/pulls?q=is%3Apr+is%3Aopen+Update+dependencies+packages+by+renovate)

### その他 renovate

やる気があれば…

#### book000

Success:

{{ book000-renovate-success-prs }}

Failure:

{{ book000-renovate-failure-prs }}

#### tomacheese

Success:

{{ tomacheese-renovate-success-prs }}

Failure:

{{ tomacheese-renovate-failure-prs }}

#### jaoafa

Success:

{{ jaoafa-renovate-success-prs }}

Failure:

{{ jaoafa-renovate-failure-prs }}
