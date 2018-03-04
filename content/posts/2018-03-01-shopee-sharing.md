---
title: "蝦皮購物新加坡研發團隊技術分享會"
date: 2018-03-01T19:51:51+08:00
thumbnail: "images/2018-03-01.jpg"
tags: ["sharing", "E-Commerce"]
description: "透過技術分享的方式順便來台灣找工程師去新加坡工作，個人是覺得這樣還算不錯，整體而言第一場技術 Lead 的分享還算不錯，雖然每個領域都只是點到為止，沒有一一深入探討，但也趁機會檢視一下平常營運系統會遇到的問題。"
---

透過技術分享的方式順便來台灣找工程師去新加坡工作，個人是覺得這樣還算不錯，整體而言第一場技術 Lead 的分享還算不錯，雖然每個領域都只是點到為止，沒有一一深入探討，但也趁機會檢視一下平常營運系統會遇到的問題。

活動：[蝦皮購物新加坡研發團隊技術分享會](https://www.facebook.com/ShopeeTW/photos/a.379836405535400.1073741828.334587866726921/817442225108147/?type=3)<br>
時間：2018/3/1(四) 19:00-21:00<br>
地點：蝦皮購物台北辦公室-信義區菸廠路88號9樓之1


## 兩年内如何把蝦皮從 0 做到 50 億 - 背後的工程難題

蝦皮新加坡研發團隊技術分享

Speaker：雷磊 Lei Lei，蝦皮新加坡總部技術負責人

 * 全球 4 千多人
 * 用戶下單時，先收錢還是先扣庫存？扣最後一個庫存後付款失敗，但已經送 Push Notification 給賣家
 * 金額數值，應該用什麼 data type 儲存？`long`
 * Android 共有多少螢幕 DPI？
 * Android WebView 和 Chrome WebKit 有什麼不同？
 * iOS 的 UIWebView 的 onscroll 事件在手指放開前不會被觸發怎麼辦？
 * Redis 在資料大小達到多少就無法用 bgsave 有效存擋？ `64GB`
 * Redis 有哪些指令在 production 上是不能用？`keys`
 * ***功能容易，效能難***
	 * 用 Python+Django 如何提高吞吐量？`Async`
	     * Sars: 這不是一開始開發就要做的嗎...
	 * 什麼系統架構適合透過增加伺服器數量來擴充效能？`Stateless`
	 * Load Balancer 效能瓶頸如何解？
	 * 一天 25TB 的 log 量，如何查？ `正在解...`
	 * 一個 MySQL Cluster 裡 Master Slave 哪個壓力大？`Slave`
	     * 因為 Shopee 應用場景 Read 多於 Write
	 * 一個 MySQL table 多大後就必須 sharding？
	 * 一個 MySQL database 多大後就必須分庫？
	 * MySQL 跨庫的 transacrtion 怎麼解？`還沒做到`
 * ***快取容易，清快取難***
	 * 庫存數量若有 cache，什麼時候更新比較好？
	 * 哪一類內容一定要寫入 Comment？ `未來該注意的事情，而不是看程式碼就可以知道的東西`
 * 持久發展的研發團隊：Knowledge、Cluture
	 * 技術課程和分享（錄影、課後練習）
 * 做事的同時，把人做好
 * 保持開放心態，向他人學習
 * 尊重事實 fect 和邏輯 logic
 * 充分信任其他團隊，並肩作戰
 * 可靠：言出必行，做不到也行`但要早點說`
 * 對於任何問題，一定要研究到底
	 * 找到 root cause
 * 保持好奇心，研究新技術，但不盲從
 * 犯錯時，分析、修復、紀錄、不犯第二次
 * 短期做產品，長期做平台

享受過程！

### Q&A

* 有招聘資安人員，也有黑箱、白箱入侵測試，以及外部人員回報機制
* 新加坡人口較少，Talent Pool 台灣比較多
* 研發中心在新加坡及深圳

## 台灣籍蝦皮員工經驗分享

### Ken, Taiwan Country Product Manager

* PM 分 Country PM 及 Functional PM，Country PM 會找熟悉當地文化的人
* 總部與當地營運團隊溝通橋樑
* 台灣的便利商店是個特色物流體系
* 台灣的銀行還在用 Big5，轉帳需要姓名會出錯
* 貨到付款 (COD) 在越南，東西交貨時可以先檢查再決定是否收下
* 泰國前三大社群軟體 Line、Facebook、Instagram，而 Instagram 也是交易平台
* 印尼超過 50% 的人沒有銀行帳號及信用卡，額外推出無卡信用分期付款
* 產品需適應當地文化（宗教、在地經驗）
* 有效及舒服的溝通技巧

### 郭至中 Chih-Chung Kuo，Software Engineer - Server Backend

* 台大資工 B99，1y3m，第一份工作就在蝦皮
* 去年年中之後 deploy 流程已經有改善

嗯... 跟我一樣就是個不擅長講話的工程師，也沒有準備簡報所以內容也就比較沒組織。

### 徐合邦 Ho-Pang，Data Engineer

* 之前在做 Browser 的公司... (咦
* 強調溝通風氣的重要性

剛到職約三個月，應該原本已經是 Senior 等級但換了技術領域，頗厲害的。

### HR

* 年假 18 天
* 到分公司做事的機會
* 公司會幫忙處理 Working Visa
* 薪水超過 6000 新幣（約 132,000 新台幣），可申請依親簽證，家人就可以直接在當地工作
* 工作六個月後申請長期居留，可買房子，買房可能比台灣便宜

<hr>

同場加映：

* [蝦皮燒錢 母公司虧損擴大](https://money.udn.com/money/story/5599/3005391)
* [蝦皮今年GMV目標倍增上看2350億，台灣市場的交易量占比持續下滑](https://www.bnext.com.tw/article/48321/shopee-2018-gmv-guidance-8-billion-usd)
