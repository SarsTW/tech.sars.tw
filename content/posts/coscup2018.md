---
title: "COSCUP 2018"
date: 2018-08-12T23:15:27+08:00
thumbnail: "images/COSCUP2018.jpg"
tags: ["coscup", "blockchain"]
description: "COSCUP 2018"
---

## COSCUP2018

這邊只能算是速記，這兩天晚上也沒時間整理成比較完整的筆記，未來應該也不會有機會整理了。

第一天幾乎都聽區塊鏈，第二天早上閒晃居多，下午跑去另一場活動，雖然還是有其他想聽的議程，但也就懶得跑來跑去了。

* 儘量不要用合約呼叫合約（Reentrance）
* ERC223、ERC677
* ERC777 (ERC820)
 * 增加 Operator 角色，讓第三方代管 token
* Transaction pool
 * Local vs Remote
     * Local: from this node, keep always
     * Remote: from other nodes, might be dropped when pool full
 * Pending vs Queue
     * Pending: ready and included in the block
     * Queued: transaction nonce is not in sequence
* Block gas limit: ~ 8,000,000
* Empty block is valid
* eth-indexer: 
 * https://github.com/getamis/eth-indexer
 * https://medium.com/getamis/%E5%A6%82%E4%BD%95%E5%BB%BA%E7%AB%8B-etherscan-%E6%9C%8D%E5%8B%99-c79c847ec4f
* 公有鍊問題（UPS 問題）
* 雷電網路 - Channel life cycles
 * Open channel
 * Join channel (deposit, init state)
 * Off-chain transfers (update)
 * Close channel (submit final state)
 * Chanllenge period (for security)(timelock)
 * Settle (withdrawal)
* Payment Channel
* Ethereum Plasma
 * Map-Reduce
 * Fraud proof: challenge misbehavior
 * Different business logic could launch diff Plasma system
* litylang.org
* Lity 解 Overflow
 * VM 層級
 * Compiler 層級
* ERC223 auth modifier 漏洞
* Gas 收費組成：Gas 基本費 21000，傳輸的資料，執行的運算
 * 空合約 - 42901
 * ERC20 Token - 697051
 * 刪除 -24000
* 資料儲存
 * 新增: 20000
 * 修改 5000
 * 刪除 -15000 (仍算一次修改）
     * 將非 0 值改 0
 * 至少要一半費用
 * 256 Bits 每四個寫入一次
* 每 byte 算 68 Gas
* 可更新的智能合約
 * 佈署新合約，把舊的合約的帳戶資料放到新的合約，但資料不容易轉移
 * 將邏輯和資料分開（Logic Conntract、Data Conntract）
     * Data contract (getter/setter) owned by logic contract (upgradeable)
     * Transfer owner of data contract
     * 用 ENS 指向 logic contract，對外用 ENS，更新時只需要將名稱指向新合約
 * Proxy
     * Delegate Call
     * Logic Contract + Proxy Contract
     * 更改 proxy contract 內儲存的合約地址變數
 * Zeppelin_os https://zeppelinos.org
 * 更新的信任問題
* NERVOS
* Information -> Blockchain Token
 * Valuable + Verfied + Ownership

### Slide

* [區塊鏈上的二手票劵售票系統](https://docs.google.com/presentation/d/1j0NM_ZDc-7_ImVro3eauKThlj2CjhUqB2QKPrpBuGiM/edit?usp=sharing)