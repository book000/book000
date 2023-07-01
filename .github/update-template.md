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
wget -qO /opt/calculate-disk.sh https://gist.githubusercontent.com/book000/d24fd6d6b832f8be28e7d7d8b9b48512/raw/calculate-disk.sh && bash /tmp/calculate-disk.sh && rm /opt/calculate-disk.sh
```

Linux 系サーバでは ncdu を定期実行している環境もあるので、`ncdu -f /ncdu.json` などで詳細を確認。  

## PC / Server のアップデート

適宜 Windows Update などを適用

| ✅ | ComputerName | OS              | PM  |
| :---: | ------------ | --------------- | --- |
|  | 🍓 ICHIGO       | Windows         |     |
|  | 🍫 CHOCO        | Windows         |     |
|  | 🍌 BANANA       | Windows         |     |
|  | 🍃 MINT         | Windows         |     |
|  | 🥧 TomaPi       | Raspberry Pi OS | apt |
|  | 🍊 ORANGE     | Ubuntu          | apt |
|  | 🥜 Nuts         | Ubuntu          | apt |
|  | 🌉 frp-server   | Ubuntu          | apt |
|  | ☄ Comet        | Ubuntu          | apt |

### Windows

```powershell
# Windows
start ms-settings:windowsupdate # Settings -> Update & Security -> Windows Update の画面を開く

## コマンドラインだけでやるなら...
Install-Module PSWindowsUpdate
Get-WindowsUpdate | tee windows-update-2023-06-01.log
Install-WindowsUpdate
```

### 🥧 TomaPi

```shell
wget -qO monthly-update.sh "https://api.tomacheese.com/monthly-update.sh?update_type=apt-upgrade&number={{ pr-number }}&machine_emoji=🥧&machine_name=TomaPi&date={{ date }}" && bash monthly-update.sh
```

### 🍊 ORANGE

```shell
wget -qO monthly-update.sh "https://api.tomacheese.com/monthly-update.sh?update_type=apt-upgrade&number={{ pr-number }}&machine_emoji=🍊&machine_name=ORANGE&date={{ date }}" && bash monthly-update.sh
```

### 🥜 Nuts

```shell
wget -qO monthly-update.sh "https://api.tomacheese.com/monthly-update.sh?update_type=apt-upgrade&number={{ pr-number }}&machine_emoji=🥜&machine_name=Nuts&date={{ date }}" && bash monthly-update.sh
```

### 🌉 frp-server

```shell
wget -qO monthly-update.sh "https://api.tomacheese.com/monthly-update.sh?update_type=apt-upgrade&number={{ pr-number }}&machine_emoji=🌉&machine_name=frp-server&date={{ date }}" && bash monthly-update.sh
```

### ☄ Comet

```shell
wget -qO monthly-update.sh "https://api.tomacheese.com/monthly-update.sh?update_type=apt-upgrade&number={{ pr-number }}&machine_emoji=☄&machine_name=Comet&date={{ date }}" && bash monthly-update.sh
```

## 🍓 ICHIGO Scoop

```powershell
# 管理者権限で実行
irm "https://api.tomacheese.com/monthly-update.ps1?update_type=scoop-update&number={{ pr-number }}&machine_emoji=🍓&machine_name=ICHIGO&date={{ date }}" | iex
```

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
