---
title: "[GoLang] 用 Mgo 遇到的問題與 Mgo 專案現況"
date: 2017-12-29T18:50:43+08:00
thumbnail: ""
tags: ["mgo", "golang", "mongodb"]
description: ""
---

## Primary Failover Issue

用 GoLang 連 MongoDB 大部分會使用 [mgo](https://github.com/go-mgo/mgo)，最近遇到一個問題是，mgo 在連 MongoDB Cluster 的時候，由於 MongoDB rolling update 時，Primary 會換手（Failover）幾次，這會導致 mgo 在連線時會出現 `EOF` 錯誤。

找了些資料，看起來是 mgo 在重連 Primary 之後，並不會將連線狀態重設，需要程式自己手動重設，但是連線中斷時 mgo 本身不會知道，真正用到連線時連線失敗後才會知道，又無法知道什麼時候可以重設連線，不知道有沒有什麼好解法...

## Project Status

Mgo 專案的 v2 branch 在 2016/08/18 之後已經沒有新的 commit，而作者也在 2017/03/31 在 [Project status](https://github.com/go-mgo/mgo/issues/416) 這個 Issue 內回答到 mgo 專案目前的現況，大致來說就是原作者不打算繼續維護了。目前看到 GlobalSign 這間公司 [Fork 出來的版本](https://github.com/globalsign/mgo) 還陸續有在修正問題，似乎也要考慮要不要轉換過去了。

# Reference
* [How to handle disconnections to mongodb server? (aka. autoconnect)](https://groups.google.com/forum/#!topic/mgo-users/XM0rc6p-V-8)
* [mgo 的 session 與連接池](https://cardinfolink.github.io/2017/05/17/mgo-session/)
