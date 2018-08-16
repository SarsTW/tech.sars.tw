---
title: "Ethereum 以太坊區塊鏈"
date: 2018-06-07T14:13:33+08:00
draft: true
thumbnail: ""
tags: ["ethereum", "solidity", "blockchain"]
description: ""
---

* [How does Ethereum work, anyway?](https://medium.com/@preethikasireddy/how-does-ethereum-work-anyway-22d1df506369) ([中文翻譯](https://mp.weixin.qq.com/s?__biz=MzU2ODQzNzAyNQ==&mid=2247484235&idx=1&sn=f575a7701df76c8a7d7a4d70796373db))

## Smart Contract

* [Ethereum Smart Contract Security Best Practices](https://consensys.github.io/smart-contract-best-practices/)
 * GitHub [ConsenSys/smart-contract-best-practices](https://github.com/ConsenSys/smart-contract-best-practices)
* [RBAC-SC: Role-Based Access Control Using Smart Contract](https://ieeexplore.ieee.org/document/8307397/)

### [Solidity](https://solidity.readthedocs.io/en/latest/)

* [Truffle](http://truffleframework.com) The most popular Ethereum development framework
 * [Truffle Boxes](https://truffleframework.com/boxes) example applications and project templates
* [什麼是智能合約(Smart Contract)?](https://blog.gasolin.idv.tw/2017/09/02/what-is-smart-contract/)
* [如何撰寫智能合約(Smart Contract)?(I)](https://blog.gasolin.idv.tw/2017/09/06/howto-write-a-smart-contract/)
* [如何撰寫智能合約(Smart Contract)?(II)建立加密代幣](https://blog.gasolin.idv.tw/2017/09/11/howto-write-a-simple-token/)
* [如何撰寫智能合約(Smart Contract)?(III)建立標準代幣](https://blog.gasolin.idv.tw/2017/09/16/howto-write-an-erc20-compatible-token/)
* [OpenZeppelin](https://github.com/OpenZeppelin/openzeppelin-solidity) a framework to build secure smart contracts on Ethereum
* [Ethereum 智能合約開發筆記：編譯和部署合約的第一種姿勢 - 使用 Remix](https://gist.github.com/Ankarrr/561fb3e49bd22847780fb93f0e382f59)
* [Ethereum區塊鏈！智能合約(Smart Contract)與分散式網頁應用(dApp)入門](https://legacy.gitbook.com/book/gasolin/learn-ethereum-dapp/details)

##### 亂數

由於區塊高度、timestamp 等不算是真正隨機亂數，可以加上 sender address 並 hash 過來增加亂度

##### Struct

```
struct Kitty {
    uint256 genes;
    uint64 birthTime;
    uint16 generation;
}
```

##### Modifier

```
modifier onlyOwner {
    require (msg.sender == owner);
    _;
}
```
* [Solidity Modifier Tutorial - Control Functions with Modifiers](https://coursetro.com/posts/code/101/Solidity-Modifier-Tutorial---Control-Functions-with-Modifiers)


#### Samples
* [EtherTW/LogoVote2017](https://github.com/EtherTW/LogoVote2017)
* [EtherTW/tickets](https://github.com/EtherTW/tickets) A Dapp for meetup tickets
* Taiwan Digital Token (TWDT-ETH)
 * [0x35A4e77aE040AFc9743157911d39D1451cF2F05d](https://etherscan.io/address/0x35a4e77ae040afc9743157911d39d1451cf2f05d)
 * [0x381eC72ebf803cb517285990955b2453d0529c46](https://etherscan.io/address/0x381ec72ebf803cb517285990955b2453d0529c46)
* [ICO-tutorial](https://github.com/bitfwdcommunity/ICO-tutorial/blob/master/ico-contract.sol)
* [Binance BNB contract](https://etherscan.io/address/0xB8c77482e45F1F44dE1745F52C74426C631bDD52#code)
* [GolemToken Contract](https://etherscan.io/address/0xa74476443119A942dE498590Fe1f2454d7D4aC0d)

### Multi-Signature Wallet

* [Ethereum Multi-Signature Wallets](https://medium.com/hellogold/ethereum-multi-signature-wallets-77ab926ab63b)
* [Ethereum multi-sig wallets Part II](https://medium.com/hellogold/ethereum-multi-sig-wallets-part-ii-19077f6280a)
* [GitHub - gnosis/MultiSigWallet](https://github.com/gnosis/MultiSigWallet)

### [Vyper](https://github.com/ethereum/vyper)

New experimental programming language

* 

## EIPs

### [ERC20 Token Standard](https://theethereum.wiki/w/index.php/ERC20_Token_Standard)

* [GitHub Issue - ERC: Token standard #20](https://github.com/ethereum/EIPs/issues/20)
* [GitHub Issue - ERC20 Token Standard #610](https://github.com/ethereum/EIPs/pull/610)
* [ERC20 Token使用手冊](https://medium.com/taipei-ethereum-meetup/3d7871c58bea)
* [Ethereum ERC20 Token Standard 以太坊代幣標準介紹](https://medium.com/hackoin-taiwan/b7bc58171021)

### ERC165

### [ERC223 token standard](https://github.com/ethereum/EIPs/issues/223)

If the receiver is a contract, ERC223 token contract will try to call tokenFallback function on receiver contract. If there is no tokenFallback function on receiver contract transaction will fail.

* [Recommended implementation](https://github.com/Dexaran/ERC223-token-standard/tree/Recommended)
* [ERC20 vs ERC223. List of differences](https://ethereum.stackexchange.com/questions/17054/erc20-vs-erc223-list-of-differences)

會造成 false positive 的結果而未被採用。

### [Istanbul Byzantine Fault Tolerance #650](https://github.com/ethereum/EIPs/issues/650)

### [Non-fungible Token Standard #721](https://github.com/ethereum/eips/issues/721)

### [ERC865: Pay transfers in tokens instead of gas, in one transaction](https://github.com/ethereum/EIPs/issues/865)

Ability for token holders to pay transfer transactions in tokens instead of gas, in one transaction.

### [ERC875 for non fungible tokens and simple atomic swaps](https://github.com/ethereum/EIPs/issues/875) 

* [ERCTokenImplementation](https://github.com/alpha-wallet/ERC875-Example)
* [ERC875, a new standard for non fungible tokens and cheap atomic swaps](https://medium.com/alphawallet/erc875-a-new-standard-for-non-fungible-tokens-and-cheap-atomic-swaps-93ab85b9e7f9)
* [ERC875 Token Factory
](https://alpha-wallet.github.io/ERC875-token-factory/index.html)

### [ERC: Crypto Item Standard #1155](https://github.com/ethereum/EIPs/issues/1155)

A standard interface for multiple item/token definitions in a single deployed contract.

## Some White Papers

* [JOYSO](https://joyso.io/whitepaper_zh-TW.pdf)
* [Muzeum](https://medium.com/@muzeumproject/white-paper-2cee4b0f2205)
* [CryptoDT - TWDT-ETH](https://www.cryptodt.io/pdf/TWDT_Proposals_V1.5.pdf)
* [CyberMiles: A Next Generation Blockchain Protocol for Business Transactions](https://www.cybermiles.io/wp-content/uploads/2018/03/Technical-Whitepaper_en-US.pdf)
* [HashNET: Beyond Blockchain Technology](https://tolar.io/wp-content/uploads/2018/06/HashNET_whitepaper_v03.pdf) - 2018-02
* [HashFuture](https://www.hashfuture.io/static/images/White_Paper.pdf)
* [Ubex: Artificial Intelligence in Advertising](https://icorating.com/upload/whitepaper/14TSNaz1FewCoSV4iYCzKAGpGZsX4XshZMI0Is9L.pdf)
 * [Ubex Token Economics](https://www.ubex.com/wp/Ubex-Token-Economics.pdf)
 * [https://icorating.com/ico/ubex-ubex/](https://icorating.com/ico/ubex-ubex/)
* [Electronic PK Chain](http://epc.im/epc.pdf)

## [Decentralized Autonomous Organization](https://www.ethereum.org/dao) (DAO)

* [Testing for Reentrancy attacks in remix](https://ethereum.stackexchange.com/questions/28945/testing-for-reentrancy-attacks-in-remix)

## Dapp

### HD Wallet

一組主私鑰建立許多子私鑰，透過一份seed產生多組子私鑰，轉移錢包時只需要主私鑰。

* [BIP32 Hierarchical Deterministic Wallets](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)
* [BIP44 Multi-Account Hierarchy for Deterministic Wallets](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki)
 * 提供 5 個階層，包括多幣種
 * `m / purpose' / coin_type' / account' / change / address_index`
* [HD Wallet](https://medium.com/@bun919tw/hd-wallet-970096a6d72f)
* [【加密貨幣錢包】從 BIP32、BIP39、BIP44 到 Ethereum HD Wallet](https://medium.com/taipei-ethereum-meetup/a40b1c87c1f7)
* [So you want to build an Ethereum HD wallet?](https://medium.com/bitcraft/so-you-want-to-build-an-ethereum-hd-wallet-cb2b7d7e4998)

### Mnemonic code

列出錢包助記詞及產生規則。

* [BIP39 Mnemonic code for generating deterministic keys](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)
* [Mnemonic Code Converter](https://iancoleman.io/bip39/)

## Other

* [Infura](https://infura.io/) - Your Access to the Ethereum Network
 * 除了自己用 geth 架一個以太坊節點，也可以用其他人的節點來測試或遞送交易
* [從程序員角度解釋什麼是區塊鏈的智能合約](https://block.cc/news/5b04e756ce79d2cf9b5fd683)

### DAICO: DAO + ICO

![DAICO](https://cdn-images-1.medium.com/max/1600/1*3Sgvtv8Sgl6pElCYtchmZw.png)

* [Explanation of DAICOs](https://ethresear.ch/t/explanation-of-daicos/465)
* [DAO + ICO = DAICO](https://medium.com/quillhash/dao-ico-daico-d4be2a39093c) by Preetam Rao
* [DAO + ICO = DAICO – a new way to raise funds](https://www.cointelligence.com/content/dao-ico-daico-a-new-way-to-raise-funds/)
* [【什麼是 DAICO ？】Vitalik Buterin 提出新的 ICO 概念，目前正在測試中](https://www.blocktempo.com/vitalik-new-idea-icos-tested/)

### [Parity](https://www.parity.io/)

* 

### [Ethereum Name System](https://ens.domains/)

* [A beginner’s guide to buying an ENS domain](https://medium.com/the-ethereum-name-service/a-beginners-guide-to-buying-an-ens-domain-3ccac2bdc770)
* [How To Assign your Ethereum Name Service Address To Your Ethereum Wallet](https://steemit.com/beyondbitcoin/@lexikon082/how-to-assign-your-ethereum-name-service-address-to-your-ethereum-wallet)

### Casper The Friendly Finality Gadget

Proof of stake on Ethereum.

https://vitalik.ca/files/casper_note.html

https://github.com/ethereum/research/blob/master/papers/casper-basics/casper_basics.pdf

https://github.com/ethereum/casper

### [Ether Cards](https://ether.cards/)

提供一組錢包，但預設私鑰是隱藏起來的，送禮的人可以放錢進去後，將卡片送人，收禮的人可以刮開私鑰然後將裡面的虛擬貨幣提領出來。
