## ストレージ確認

ストレージの使用状態を確認

| ✅ | ComputerName | Drive       | Used (Use %) | Size (Type)   |
| :-: | ------------ | ----------- | ------------ | ------------- |
|  | 🍓 ICHIGO       | `C:`         |  (%)         | 465 GB (SSD)  |
|  | 🍓 ICHIGO       | `N:`         |  (%)         | 3.63 TB (HDD) |
|  | 🍓 ICHIGO       | `S:`         |  (%)         | 465 GB (SSD)  |
|  | 🥧 TomaPi       | `/`         |  (%)         | 29 GB (SD)    |
|  | 🥧 TomaPi       | `/mnt/hdd`  |  (%)         | 2.7 TB (HDD)  |
|  | 🥧 TomaPi       | `/mnt/hdd2` |  (%)         | 5.5 TB (HDD)  |
|  | 🍊 ORANGE       | `/`         |  (%)         | 30 GB (SD)    |
|  | 🍊 ORANGE       | `/mnt/hdd`  |  (%)         | 916 GB (HDD)  |
|  | 🥜 Nuts         | `/`         |  (%)         | 234 GB (SSD)  |
|  | 🥜 Nuts         | `/mnt/hdd`  |  (%)         | 1.8 TB (HDD)  |
|  | 🥜 Nuts         | `/mnt/hdd2` |  (%)         | 687 GB (HDD)  |
|  | ☄ Comet        | `/`         |  (%)         | 99 GB (SSD)   |
|  | 💣 jaoMain      | `/`         |  (%)         | 99 GB (SSD)   |
|  | 🌐 jaoWeb       | `/`         |  (%)          | 99 GB (SSD)   |
|  | 👒 ZakuroHat    | `/`         |  (%)         | 115 GB (?)    |
|  | 👒 ZakuroHat    | `/home`     |  (%)         | 1.9 TB (HDD)  |

```shell
df -h -x tmpfs -x overlay | awk 'BEGIN { OFS="\t" } { printf "%-10s %5s %5s %5s\n",$6,$3,$5,$2 }' | tail -n +2 | sort
```

Linux 系サーバでは ncdu を定期実行している環境もあるので、`ncdu -f /ncdu.json` などで詳細を確認。  
Windows は可能なら WSL から df コマンドを実行したほうが使用率計算しなくて良いので楽。

`docker system prune -a` などでの Docker 関連ストレージ解放を行うこと。

## PC / Server のアップデート

適宜 Windows Update などを適用

| ✅ | ComputerName | OS              | PM  |
| :---: | ------------ | --------------- | --- |
|  | 🍓 ICHIGO       | Windows         |     |
|  | 🍫 CHOCO        | Windows         |     |
|  | 🍌 BANANA       | Windows         |     |
|  | 🍃 MINT         | Windows         |     |
|  | 🥧 TomaPi       | Raspberry Pi OS | apt |
|  | 🥜 Nuts         | Ubuntu          | apt |
|  | ☄ Comet        | Ubuntu          | apt |
|  | 🌉 frp-server   | Ubuntu          | apt |

```shell
# Debian / Ubuntu
sudo apt update
apt list --upgradable | tee apt-upgradable-{{ date }}.log

sudo apt upgrade

# RedHat
sudo yum check-update | tee yum-updates-{{ date }}.log

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

## 🍓 ICHIGO Scoop

```shell
scoop update # Scoopのリポジトリを更新
scoop status | tee scoop-{{ date }}.log # アップデート可能なアプリケーション一覧を表示
scoop update * # すべてのアプリケーションを更新
scoop status # アップデート後の一覧を確認
```

`scoop-{{ date }}.log` をこの issue のコメント欄に投稿しておくこと

## 🍓 ICHIGO winget

```shell
winget upgrade | tee winget-{{ date }}.log # アップデート可能なアプリケーション一覧を表示
winget upgrade [...] # アップデートしたいアプリケーションをアップデート
```

`winget-{{ date }}.log` をこの issue のコメント欄に投稿しておくこと

## MyMaid4

ワークフローが生成するプルリクエストを用いて一括アップデート

[`is:pr is:open Update dependencies packages by renovate` in `jaoafa/MyMaid4`](https://github.com/jaoafa/MyMaid4/pulls?q=is%3Apr+is%3Aopen+Update+dependencies+packages+by+renovate)

## renovate

やる気があれば…

### book000

#### Success:

{{ book000-renovate-success-prs }}

#### Failure:

{{ book000-renovate-failure-prs }}

### tomacheese

#### Success:

{{ tomacheese-renovate-success-prs }}

#### Failure:

{{ tomacheese-renovate-failure-prs }}

### jaoafa

#### Success:

{{ jaoafa-renovate-success-prs }}

#### Failure:

{{ jaoafa-renovate-failure-prs }}
