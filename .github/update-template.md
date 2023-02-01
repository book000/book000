## ストレージ確認

`df -h` などを活用し、ストレージの使用率を確認

- ICHIGO
  - [ ] `C`: 残り (Using: %)
  - [ ] `N`: 残り (Using: %)
- TomaPi
  - [ ] `/`: 残り (Using: %)
  - [ ] `/mnt/hdd`: 残り (Using: %)
  - [ ] `/mnt/hdd2`: 残り (Using: %)
- Nuts
  - [ ] `/`: 残り (Using: %)
  - [ ] `/mnt/hdd`: 残り (Using: %)
- Comet
  - [ ] `/`: 残り (Using: %)
- jaoMain
  - [ ] `/`: 残り (Using: %)
- jaoWeb
  - [ ] `/`: 残り (Using: %)
- ZakuroHat
  - [ ] `/`: 残り (Using: %)
  - [ ] `/home`: 残り (Using: %)

## アップデート

各アプリケーション等のアップデート実施

- [ ] Computer
- [ ] Scoop
- [ ] winget
- [ ] MyMaid4

### Computer / Server

適宜 Windows Update などを適用

- [ ] ICHIGO
- [ ] CHOCO
- [ ] BANANA
- [ ] MINT
- [ ] TomaPi
- [ ] Nuts
- [ ] Comet
- [ ] frp-server

```shell
# Debian / Ubuntu
sudo apt update
apt list --upgradable > apt-upgradable-{{ date }}.log

sudo apt upgrade

# RedHat
sudo yum check-update > yum-updates-{{ date }}.log

sudo yum update
```

```powershell
# Windows
start ms-settings:windowsupdate # Settings -> Update & Security -> Windows Update の画面を開く

## コマンドラインだけでやるなら...
Install-Module PSWindowsUpdate
Get-WindowsUpdate | tee windows-update-{{ date }}.log
Install-WindowsUpdate
```

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
