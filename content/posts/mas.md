---
title: "使用 Mas 安裝 Mac App Store 內的軟體"
date: 2018-02-04T22:16:58+08:00
thumbnail: "images/mas-cli.jpg"
tags: ["macOS"]
description: ""
---

[Mas](https://github.com/mas-cli/mas) 是一套可以透過指令方式操作 Mac App Store 的程式，類似於 [Homebrew](https://brew.sh/index_zh-tw.html)，對於需要批次複製安裝大量電腦，或是重新安裝 macOS 後需要一次把軟體、程式都安裝回來等需求，不用一個個慢慢裝。

搭配 Homebrew 與 mas，如果是有在 Mac App Store 上架的軟體，我會透過 mas 方式安裝，如果是沒上架的軟體，或是其他開發用到的指令，則會使用 Homebrew 來安裝，搭配使用效果雙倍！

首先需要安裝好 [Homebrew](https://brew.sh/index_zh-tw.html)，安裝方式直接參考官網一行指令就搞定。

安裝 mas 指令：

    brew install mas

裝好後馬上可以查看目前 Mac Apple Store 已經裝了哪些軟體：

    mas list

接著就跟在 Mac Apple Store 上面搜尋軟體一樣，使用 mas search 指令來找尋想安裝的軟體，例如想安裝好用的郵件軟體 Spark 就可以輸入：

    mas search spark

可能會出現很多結果，根據判斷應該會是

    1176895641 Spark - Love your email again

`1176895641` 就是 Spark 的 App ID，找到後就可以透過 mas install 來安裝它

    mas install 1176895641

另外還有 `mas outdated` 指令可以查看有哪些軟體有出新版本可以更新，然後就可以用 `mas upgrade` 指令一次更新全部，或是後面接上 App ID 只更新指定的軟體。

## Reference

* [清除重裝你的 Mac，不再遲疑](https://medium.com/@abookyun/%E6%B8%85%E9%99%A4%E9%87%8D%E8%A3%9D%E4%BD%A0%E7%9A%84-mac-%E4%B8%8D%E5%86%8D%E9%81%B2%E7%96%91-9b30ea134038)
