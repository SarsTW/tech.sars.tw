---
title: "使用 Hugo 快速建立靜態網站"
date: 2017-12-21T17:15:08+08:00
thumbnail: "images/build-static-site-hugo.png"
draft: true
---

# 安裝 Hugo
在已經安裝好 brew 環境的 macOS 上安裝 Hugo 非常容易，只需要一行指令即可完成。

	brew install hugo

# 建立 Hugo 網站專案

	hugo new site quickstart

目錄底下會多出一個 quickstart 子目錄，即是一個新網站專案。


# 新增佈景主題

Hugo 提供許多佈景主題，可以在 [Hugo Themes](https://themes.gohugo.io/) 這邊找到喜歡的佈景主題，以本站用的 [Robust](https://themes.gohugo.io/robust/) 主題為例，只需要切換到專案目錄內：

	git submodule add https://github.com/dim0627/hugo_theme_robust.git themes/robust

即可安裝，接著在 `config.toml` 檔案中將 theme 的設定值改成

	theme = "robust"

即可換成剛剛安裝的佈景主題。

# 新增一篇文章

在 Hugo 內，一個 Markdown 檔案就是一篇文章，建立文章的方式也很簡單：

	hugo new posts/my-first-post.md

然後用文字編輯器，或任何支援 Markdown 語法的編輯器，直接撰寫文章即可。

# 本機查看網站

Hugo 專案建立的靜態網站不需要先發佈到網路上才能瀏覽，可以先在本機查看成果：

	hugo server -D

在修改網站設定後，可以先透過這個方式快速預覽結果，等修改完成後再一次佈署到網路空間上。


# 參考

[Hugo - Getting Started - Quick Start](https://gohugo.io/getting-started/quick-start/)