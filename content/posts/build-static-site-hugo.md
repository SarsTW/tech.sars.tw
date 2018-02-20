---
title: "使用 Hugo 快速建立靜態網站"
date: 2017-12-22T18:45:16+08:00
thumbnail: "images/build-static-site-hugo.png"
tags: ["Hugo"]
description: "簡單來說，這個網站是透過 Hugo 產生的，是個純靜態網站（沒有後端資料庫），Hugo 產生出來的網站可以直接上傳到 GitHub Pages、Netlify 或是 CDN 上，撰寫文章透過 Markdown 語法，方便做文章控管。"
---

簡單來說，這個網站是透過 [Hugo](https://gohugo.io/) 產生的，是個純靜態網站（沒有後端資料庫），Hugo 產生出來的網站可以直接上傳到 GitHub Pages、Netlify 或是 CDN 上，撰寫文章透過 Markdown 語法，方便做文章控管。

Hugo 本身是透過 Golang 撰寫而成，另一個功能類似的專案 [Hexo](https://hexo.io/zh-tw/index.html) 則是使用 Node.js 撰寫。

# 安裝 Hugo

在已經安裝好 brew 環境的 macOS 上安裝 Hugo 非常容易，只需要一行指令即可完成。

	brew install hugo

其他平台上相對麻煩許多，這邊就先略過了...

# 建立 Hugo 網站專案

	hugo new site quickstart

目錄底下會多出一個 quickstart 子目錄，即是一個新網站專案。

每個 Hugo 的專案裡面都會有這些基本的目錄與檔案：

1. archetypes：樣板檔案，使用 `hugo new` 指令時會從這邊複製過去，並代換變數
2. content：放置文章
3. static：放圖片、影片或其他靜態檔案
4. themes：佈景主題檔案
5. config.toml：專案設定檔，Hugo 靠這個檔案判斷及運作


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

每篇文章剛建立時，預設會是草稿（draft）狀態，當文章撰寫完成後，只要將檔案前幾行設定值的 `draft: true` 整行刪除，文章就會被視為正式發佈的狀態，這樣之後才會出現在網站中。（早期使用 undraft 指令已經[整個被拔除](https://github.com/gohugoio/hugo/commit/2fa70c9344b231c9d999bbafdfa4acbf27ed9f6e)了）

# 本機查看網站

Hugo 專案建立的靜態網站不需要先發佈到網路上才能瀏覽，可以先在本機查看成果：

	hugo server -D

在修改網站設定後，可以先透過這個方式快速預覽結果，等修改完成後再一次佈署到網路空間上。

# 佈署到 Netlify 上

網站改好後，就可以放到網路上正式公開，可以自己架設伺服器來放，也可以選擇第三方服務來幫忙，Hugo 官方文件提供了 Netlify、Google Firebase、GitHub、GitLab、Bitbucket 等，這邊選擇了 Netlify，主要的考量點有幾項：
1. 免費靜態網頁空間
2. 免費自訂網域名稱（Custom Domain Name）
3. 免費 HTTPS 憑證（透過 Let's Encrypt）
4. 支援 CI/CD

在 Netlify 開一個專案並指定好 Source Code 存放的地點，並設定

	Build command: hugo
	Publish directory: public

並在 Build environment variables 區塊中設定 `HUGO_VERSION` 為 `0.26`，完成後 Netlify 就會自動從 GitHub 把檔案拉下來，用 Hugo 編譯好成品後，再佈署到伺服器上，整個過程會全自動完成，不需要再手動更新網站，最後用 Netlify 提供的網址，就可以看到網站成品了。

# 參考

* [Hugo - Getting Started - Quick Start](https://gohugo.io/getting-started/quick-start/)
* [Hugo - Hosting and Deployment - Host on Netlify](https://gohugo.io/hosting-and-deployment/hosting-on-netlify/)
