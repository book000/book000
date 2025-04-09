## ストレージ確認

ストレージの使用状態を確認

| ✅ | ComputerName | Drive | Used (Use %) | Size (Type) |
| :-: | - | - | - | - |
|  | 🍓 ICHIGO | `C:` |  (%) | 464.77 GB (SSD) | <!-- calculate-storage#ICHIGO#C: -->
|  | 🍓 ICHIGO | `N:` |  (%) | 7.28 TB (HDD) | <!-- calculate-storage#ICHIGO#N: -->
|  | 🍓 ICHIGO | `S:` |  (%) | 465.75 GB (SSD) | <!-- calculate-storage#ICHIGO#S: -->
|  | 🥧 TomaPi | `/` |  (%) | 28.39 GB (SD) | <!-- calculate-storage#tomapi#/ -->
|  | 🥧 TomaPi | `/mnt/hdd` |  (%) | 2.69 TB (HDD) | <!-- calculate-storage#tomapi#/mnt/hdd -->
|  | 🥧 TomaPi | `/mnt/hdd2` |  (%) | 5.41 TB (HDD) | <!-- calculate-storage#tomapi#/mnt/hdd2 -->
|  | 🍊 ORANGE | `/` |  (%) | 29.02 GB (SD) | <!-- calculate-storage#ORANGE#/ -->
|  | 🍊 ORANGE | `/mnt/hdd` |  (%) | 915.82 GB (HDD) | <!-- calculate-storage#ORANGE#/mnt/hdd -->
|  | 🥜 Nuts | `/` |  (%) | 233.67 GB (SSD) | <!-- calculate-storage#nuts#/ -->
|  | 🥜 Nuts | `/mnt/hdd` |  (%) | 1.79 TB (HDD) | <!-- calculate-storage#nuts#/mnt/hdd -->
|  | 🥜 Nuts | `/mnt/hdd2` |  (%) | 686.60 GB (HDD) | <!-- calculate-storage#nuts#/mnt/hdd2 -->
|  | ☄ Comet | `/` |  (%) | 98.25 GB (SSD) | <!-- calculate-storage#Comet3#/ -->
|  | 🌉 frp-server | `/` |  (%) | 29.36 GB (SSD) | <!-- calculate-storage#frp-server#/ -->
|  | ⏺️ RecPi | `/` |  (%) | 28.14 GB (SD) | <!-- calculate-storage#recpi#/ -->
|  | ⏺️ RecPi | `/mnt/hdd` |  (%) | 3.58 TB (HDD) | <!-- calculate-storage#recpi#/mnt/hdd -->
|  | 👒 ZakuroHat | `/` |  (%) | 125.43 GB (?) | <!-- calculate-storage#zh-2#/ -->
|  | 👒 ZakuroHat | `/home` |  (%) | 1.79 TB (HDD) | <!-- calculate-storage#zh-2#/home -->

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

| ✅ | ComputerName | OS              | PM  |
| :---: | ------------ | --------------- | --- |
|  | 🍓 ICHIGO       | Windows         | Scoop | <!-- update-softwares#ICHIGO#scoop -->
|  | 🥧 TomaPi       | Raspberry Pi OS | apt | <!-- update-softwares#tomapi#apt -->
|  | 🍊 ORANGE     | Ubuntu          | apt | <!-- update-softwares#ORANGE#apt -->
|  | 🥜 Nuts         | Ubuntu          | apt | <!-- update-softwares#nuts#apt -->
|  | 🌉 frp-server   | Ubuntu          | apt | <!-- update-softwares#frp-server#apt -->
|  | ☄ Comet        | Ubuntu          | apt | <!-- update-softwares#Comet3#apt -->
|  | 👒 ZakuroHat    | Ubuntu          | apt | <!-- update-softwares#zh-2#apt -->

## 🍓 ICHIGO Scoop

```powershell
# 管理者権限で実行
irm "https://api.tomacheese.com/monthly-update.ps1?update_type=scoop-update&number={{ pr-number }}&machine_emoji=🍓&machine_name=ICHIGO&date={{ date }}" | iex
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
