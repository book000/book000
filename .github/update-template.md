## ストレージ確認

ストレージの使用状態を確認

| ✅ | ComputerName | Drive       | Used (Use %) | Size (Type)   |
| :-: | ------------ | ----------- | ------------ | ------------- |
|  | 🍓 ICHIGO       | `C:`         |  (%)         | 465 GB (SSD)  | <!-- calculate-storage#ICHIGO#C: -->
|  | 🍓 ICHIGO       | `N:`         |  (%)         | 3.63 TB (HDD) | <!-- calculate-storage#ICHIGO#N: -->
|  | 🍓 ICHIGO       | `S:`         |  (%)         | 465 GB (SSD)  | <!-- calculate-storage#ICHIGO#S: -->
|  | 🥧 TomaPi       | `/`         |  (%)         | 29 GB (SD)    | <!-- calculate-storage#tomapi#/ -->
|  | 🥧 TomaPi       | `/mnt/hdd`  |  (%)         | 2.7 TB (HDD)  | <!-- calculate-storage#tomapi#/mnt/hdd -->
|  | 🥧 TomaPi       | `/mnt/hdd2` |  (%)         | 5.5 TB (HDD)  | <!-- calculate-storage#tomapi#/mnt/hdd2 -->
|  | 🍊 ORANGE       | `/`         |  (%)         | 30 GB (SD)    | <!-- calculate-storage#ORANGE#/ -->
|  | 🍊 ORANGE       | `/mnt/hdd`  |  (%)         | 916 GB (HDD)  | <!-- calculate-storage#ORANGE#/mnt/hdd -->
|  | 🥜 Nuts         | `/`         |  (%)         | 234 GB (SSD)  | <!-- calculate-storage#nuts#/ -->
|  | 🥜 Nuts         | `/mnt/hdd`  |  (%)         | 1.8 TB (HDD)  | <!-- calculate-storage#nuts#/mnt/hdd -->
|  | 🥜 Nuts         | `/mnt/hdd2` |  (%)         | 687 GB (HDD)  | <!-- calculate-storage#nuts#/mnt/hdd2 -->
|  | ☄ Comet        | `/`         |  (%)         | 99 GB (SSD)   | <!-- calculate-storage#Comet3#/ -->
|  | 🌉 frp-server   | `/`         |  (%)         | 29.36 GB (SSD) | <!-- calculate-storage#frp-server#/ -->
|  | ⏺️ RecPi        | `/`         |  (%)         | 30 GB (SD)    | <!-- calculate-storage#recpi#/ -->
|  | ⏺️ RecPi        | `/mnt/hdd`  |  (%)         | 3.6 TB (HDD)  | <!-- calculate-storage#recpi#/mnt/hdd -->
|  | 👒 ZakuroHat    | `/`         |  (%)         | 115 GB (?)    | <!-- calculate-storage#zh-2#/ -->
|  | 👒 ZakuroHat    | `/home`     |  (%)         | 1.9 TB (HDD)  | <!-- calculate-storage#zh-2#/home -->

### Windows

```powershell
$env:ISSUE_NUMBER={{ pr-number }}; irm https://raw.githubusercontent.com/book000/calculate-storage/refs/heads/master/calculate-storage.ps1 | iex
```

### Linux

```shell
wget -qO - https://raw.githubusercontent.com/book000/calculate-storage/refs/heads/master/calculate-storage.sh | sudo ISSUE_NUMBER={{ pr-number }} bash
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
|  | 👒 ZakuroHat    | Ubuntu          | apt |

### Windows

```powershell
# Windows
start ms-settings:windowsupdate # Settings -> Update & Security -> Windows Update の画面を開く

## コマンドラインだけでやるなら...
Install-Module PSWindowsUpdate
Get-WindowsUpdate | tee windows-update-2023-06-01.log
Install-WindowsUpdate
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

### ☄ Comet

```shell
wget -qO monthly-update.sh "https://api.tomacheese.com/monthly-update.sh?update_type=apt-upgrade&number={{ pr-number }}&machine_emoji=☄&machine_name=Comet&date={{ date }}" && bash monthly-update.sh
```

### 🌉 frp-server

```shell
wget -qO monthly-update.sh "https://api.tomacheese.com/monthly-update.sh?update_type=apt-upgrade&number={{ pr-number }}&machine_emoji=🌉&machine_name=frp-server&date={{ date }}" && bash monthly-update.sh
```

### 👒 ZakuroHat

```shell
wget -qO monthly-update.sh "https://api.tomacheese.com/monthly-update.sh?update_type=apt-upgrade&number={{ pr-number }}&machine_emoji=👒&machine_name=ZakuroHat&date={{ date }}" && bash monthly-update.sh
```

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
