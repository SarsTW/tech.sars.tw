---
title: "20210325 Jamf Apple Device Management Camp"
date: 2021-03-25T13:42:53+08:00
thumbnail: "/images/2021/2021-03-25.jpg"
tags: ["jamf"]
description: ""
---

## Update, Upgrade, Factory Reset

- Command-R - Start up macOS Recovery (Update)
- Option-Command-R - Start up macOS Recovery over the Internet (Upgrade to latest supported)
- Shift-Option-Command-R - Start up macOS Recovery over the Internet (Shipped version)


## Startup Security Utility

Apple T2 Security Chip

可禁止安裝雙系統開機、禁止外接硬碟開機等。

## 安裝方式

- App Store
- macOS Recovery
- createinstallmedia
- startosinstall
- MDM

非正規方式（無法驗證、信任）

- 打包 Image
- Installing macOS on a Mac in target disk mode

## FileVault

建議企業統一預設開啟，且不可被關閉。

開啟不會影響系統效能。

Jamf 會統一管理 FileVault Recovery Key。

## System Extension 取代 Kernel Extension

避免沙盒機制被 Kernel Extension 繞過。

# jamf

[iMazing Profile Editor](https://imazing.com/profile-editor) 可以自己編寫 Profile 檔案
