---
title: "Hyperledger 超級帳本"
date: 2018-05-06T17:16:49+08:00
draft: true
thumbnail: ""
tags: ["hyperledger", "blockchain"]
description: ""
---

# Hyperledger

Blockchain Technologies For Business

* [Enterprise adoption patterns - Use case examples from practice - Into Hyperledger Fabric v1 (Hyperledger Meetup)](https://www.hyperledger.org/wp-content/uploads/2017/05/HL_Meetup_Blockchain_IBM__Mai_v2a-1.pdf)
* [IBM技术专家：Hyperleger Fabric 架构与部署实例解析](https://mp.weixin.qq.com/s?__biz=MzU2ODQzNzAyNQ==&mid=2247483894&idx=1&sn=2b29bc68ed51de365775c9a27846a4b4)
* [一文理解超級賬本Hyperledger Fabric的架構與坑](https://mp.weixin.qq.com/s?__biz=MzU2ODQzNzAyNQ==&mid=2247483932&idx=1&sn=8c1993bec84cb9c526da725bc6bccb39)

## Consortium Blockchain

## Smart Contracts

* [Hyperledger Architecture, Volume II, Smart Contracts](https://www.hyperledger.org/wp-content/uploads/2018/04/Hyperledger_Arch_WG_Paper_2_SmartContracts.pdf)

## Hyperledger Fabric

* [Hyperledger Fabric GitHub](https://github.com/hyperledger/fabric)
* [Hyperledger Fabric Docs](http://hyperledger-fabric.readthedocs.io/en/release-1.2/)

### Components

* Membership Service Provider(MSP)
* Peer
* Order
* Channel
* Chaincode
* Participants
* Assets
* Transactions
* Endorser
* Committer
* Submitter

### Docker Images

1.1.0

`$ curl -sSL https://goo.gl/6wtTN5 | bash -s 1.1.0`

```
REPOSITORY                      TAG             IMAGE ID            CREATED             SIZE
hyperledger/fabric-ca           x86_64-1.1.0    72617b4fa9b4        2 months ago        299MB
hyperledger/fabric-tools        x86_64-1.1.0    b7bfddf508bc        2 months ago        1.46GB
hyperledger/fabric-orderer      x86_64-1.1.0    ce0c810df36a        2 months ago        180MB
hyperledger/fabric-peer         x86_64-1.1.0    b023f9be0771        2 months ago        187MB
hyperledger/fabric-javaenv      x86_64-1.1.0    82098abb1a17        2 months ago        1.52GB
hyperledger/fabric-ccenv        x86_64-1.1.0    c8b4909d8d46        2 months ago        1.39GB
hyperledger/fabric-zookeeper    x86_64-0.4.6    92cbb952b6f8        3 months ago        1.39GB
hyperledger/fabric-kafka        x86_64-0.4.6    554c591b86a8        3 months ago        1.4GB
hyperledger/fabric-couchdb      x86_64-0.4.6    7e73c828fc5b        3 months ago        1.56GB
```

1.0.0

```
REPOSITORY                      TAG             IMAGE ID            CREATED             SIZE
hyperledger/fabric-tools        x86_64-1.0.0    0403fd1c72c7        9 months ago        1.32GB
hyperledger/fabric-couchdb      x86_64-1.0.0    2fbdbf3ab945        9 months ago        1.48GB
hyperledger/fabric-kafka        x86_64-1.0.0    dbd3f94de4b5        9 months ago        1.3GB
hyperledger/fabric-zookeeper    x86_64-1.0.0    e545dbf1c6af        9 months ago        1.31GB
hyperledger/fabric-orderer      x86_64-1.0.0    e317ca5638ba        9 months ago        179MB
hyperledger/fabric-peer         x86_64-1.0.0    6830dcd7b9b5        9 months ago        182MB
hyperledger/fabric-javaenv      x86_64-1.0.0    8948126f0935        9 months ago        1.42GB
hyperledger/fabric-ccenv        x86_64-1.0.0    7182c260a5ca        9 months ago        1.29GB
hyperledger/fabric-ca           x86_64-1.0.0    a15c59ecda5b        9 months ago        238MB
```

### Building Your First Network

`cd fabric-samples/first-network`

`./byfn.sh -m generate`

`./byfn.sh -m up`

`./byfn.sh -m down`

### Deploy

* GitHub - [blockchain-network-on-kubernetes](https://github.com/IBM/blockchain-network-on-kubernetes)
* [Deploy Hyperledger Fabric on Kubernetes Part 1](http://www.think-foundry.com/deploy-hyperledger-fabric-on-kubernetes-part-1/)
* [Deploy Hyperledger Fabric on Kubernetes Part 2](http://www.think-foundry.com/deploy-hyperledger-fabric-on-kubernetes-part-2/)

## [Hyperledger Composer](https://hyperledger.github.io/composer/latest/)

* [Hyberledger Composer GitHub](https://github.com/hyperledger/composer)
* [Installing the development environment](https://hyperledger.github.io/composer/latest/installing/development-tools.html)

## Hyperledger Cello

## Hyperledger Caliper

A blockchain benchmark framework to measure performance of multiple blockchain solutions.

[GitHub](https://github.com/hyperledger/caliper)

## Hyperledger News

* [Hyperledger Fabric 1.0版推出，區塊鏈將進入黃金時代](http://iknow.stpi.narl.org.tw/Post/Read.aspx?PostID=13580)
* [第一個開發成熟的商用區塊鏈開源框架Hyperledger Fabric 1.0上線！](https://www.bnext.com.tw/article/45355/hyperledger-fabric-releases-version-1-0-of-open-source-distributed-ledger)
* [全球海運龍頭快桅宣布採用IBM區塊鏈技術，大幅減少繁瑣的人工作業](https://www.bnext.com.tw/article/43486/maersk-apply-blackchain-reducing-cost)
* [IBM力挺，全球最大區塊鏈聯盟Hyperledger會員突破122名](https://www.bnext.com.tw/article/43517/blockchain-ibm-hyperledger)
* [Hyperledger Fabric 架構已成熟，IBM 有信心：2017 是區塊鏈應用落實年](http://technews.tw/2017/03/12/ibm-says-blockchain-will-imply-extensively-in-2017/)

## Blockchain as a Service

* [點融區塊鏈雲服務平台 ](https://baas.dianrong.com)
