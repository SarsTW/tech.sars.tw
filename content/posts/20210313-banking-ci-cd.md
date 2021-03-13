---
title: "20210313 GDG Taipei"
date: 2021-03-13T15:09:31+08:00
thumbnail: "/images/2021/2021-03-13.jpg"
tags: ["ci/cd", "gitops", "devops", "gitlab"]
description: ""
---

地點：愛料理（台北市中正區羅斯福路二段9號9F）

講者：永豐金證券 生魚片、GitLab TW Community core member 印章

活動：[https://gdg.community.dev/events/details/google-gdg-taipei-presents-jin-rong-tuan-dui-ru-he-liu-chang-dao-ru-cicd-gitops/](https://gdg.community.dev/events/details/google-gdg-taipei-presents-jin-rong-tuan-dui-ru-he-liu-chang-dao-ru-cicd-gitops/)

# 金融團隊如何流暢導入 CI/CD & GitOps

- 2004 年的換板工具（上傳檔案）
- 降低人為的操作、減少人為失誤
- GitLab stages 包含編譯、佈署與退版
- Windows 的 Binary 檔案有 PE Header 導致編譯出來的檔案每次都會不一樣，造成 CI 會視為不同的檔案而全部重新編譯
- Artifacts 管理

[Shioaji](https://sinotrade.github.io) - the most pythonic API for trading the Taiwan and global financial market

<iframe src="https://onedrive.live.com/embed?cid=A5F1134510BD0289&resid=A5F1134510BD0289%2133021&authkey=ANQV4N4MioZUqMg&em=2" width="476" height="288" frameborder="0" scrolling="no"></iframe>

# GitOps 導入

- 吳易璋 seal.tw
- GitLab is a DevOps platform，已經不是單純的 Source Code Management
- GitOps = IaC + MRs + CI/CD
 - IaC: Ansible, Chef (Omnibus), Terraform, Docker Compose, Kubernetes
 - MRs: Merge Request, PR, GitLab Flow
 - CI/CD: GitLab CI

