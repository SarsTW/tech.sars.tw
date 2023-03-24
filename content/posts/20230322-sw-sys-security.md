---
title: "2023/03/22 安全軟體開發與系統安全監控及檢測技術"
date: 2023-03-22T09:04:55+08:00
thumbnail: "images/2023/2023-03-22.jpg"
tags: ["security"]
description: ""
---

講師： 大同大學資工系 包教授

地點：中華民國資訊軟體協會

教材： https://webhd3.ttu.edu.tw 識別名稱： `20230322課程`

---

Source Code 檢測

- 針對 C 語言比較有效（Pointer 等）
- PHP / Java / .NET 比較沒有基本問題（Legacy Function、Library 有問題）

弱點掃描

- 作業系統版本
- 網頁伺服器、執行環境版本

## 安全軟體開發生命週期 SSDLC

- 登入頁：使用者登入失敗時，顯示「帳號 或 密碼錯誤」
- 查無帳號時，仍然要紀錄錯誤，可以知道是否正遭受暴力破解
- 個資最小搜集

Resource:

- [https://sites.google.com/email.nchu.edu.tw/ssdlc](https://sites.google.com/email.nchu.edu.tw/ssdlc)
- [https://docs.google.com/spreadsheets/d/1qcTVKOGL1vpUlyfLeA10C8Dq0Gdddl8d4Sluqi_KYI8/](https://docs.google.com/spreadsheets/d/1qcTVKOGL1vpUlyfLeA10C8Dq0Gdddl8d4Sluqi_KYI8/)
- [https://www.youtube.com/watch?v=3juFKVhd5Bg](https://www.youtube.com/watch?v=3juFKVhd5Bg)

### STRIDE
- Spoofing
- Tempering
- Repudiation
- Information Disclosure
- DoS
- Elevation of Privilege

## 實作

1. 安裝 Virtualbox、Kali Linux：[https://ithelp.ithome.com.tw/articles/10298620](https://ithelp.ithome.com.tw/articles/10298620)

2. 安裝 Metasploitable 2：[https://ithelp.ithome.com.tw/articles/10299666](https://ithelp.ithome.com.tw/articles/10299666)

3. 易卡關： 

    Guest OS 的設定中，啟用 System 中 Processor 分頁內的「Enable PAE/NX」，且 CPU 只能給一個，如果要給多個 CPU，要在 Grub 設定 kernel 啟動時加上 `noacpi` 

    （設定方式： [https://www.youtube.com/watch?v=aYxfhMrjVhk](https://www.youtube.com/watch?v=aYxfhMrjVhk) ）

### Metasploitable

- GitHub - [spvreddy / metasploitable-solutions ](https://github.com/spvreddy/metasploitable-solutions)
- [Metasploit Unleashed](https://www.offsec.com/metasploit-unleashed/)

### Nessus Essentials

剛安裝好啟動後，需要等一段時間背景編譯一些套件。

### [Proxmox VE](https://www.proxmox.com/en/)

- [https://ithelp.ithome.com.tw/articles/10237930](https://ithelp.ithome.com.tw/articles/10237930)

