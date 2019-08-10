---
title: "透過 GitLab CI/CD 上傳 Docker Image 到 GCP GCR 並 Deploy 到 GKE"
date: 2019-08-10T19:21:29+08:00
thumbnail: "images/2019-08-10-GitLab-CI-to-GCR-and-K8s.png"
tags: ["gitlab", "ci/cd", "kubernetes", "gcp"]
description: ""
---

一直很想把 CI/CD 流程整進去新架設的 Kubernetes 內（透過 GKE 提供的），花了點時間終於搞定了。

建立 Service Account，產生 JSON 格式的 private key，並給予 GCR 及 GKE 權限，分別拿來上傳編譯好的 Docker Image 以及操作 GKE。整個流程大致上如最上面的圖片，其實不難，只是中間如果有東西沒串好，整個流程就不會動。

建立 Kubernetes Role 並綁定 RBAC，這邊設定 extensions/deployments 給予 get/patch/list 權限。

```
kind: Role
apiVersion: rbac.authorization.k8s.io/v1beta1
metadata:
  namespace: default
  name: deployment-manager-gitlab
rules:
- apiGroups: ["extensions"]
  resources: ["deployments"]
  verbs: ["get", "patch", "list"]
---
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1beta1
metadata:
  name: deployment-manager
  namespace: default
subjects:
- kind: User
  name: "[[前面建立的 IAM 帳號]]"
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: deployment-manager-gitlab
  apiGroup: rbac.authorization.k8s.io
```

透過 kubectl apply 設定後，確認 RBAC 綁定狀況：

`# kubectl get Role,RoleBinding`

```
NAME                                                       AGE
role.rbac.authorization.k8s.io/deployment-manager-gitlab   138m
role.rbac.authorization.k8s.io/nginx-ingress               14d

NAME                                                       AGE
rolebinding.rbac.authorization.k8s.io/deployment-manager   138m
rolebinding.rbac.authorization.k8s.io/nginx-ingress        14d
```

設定 GitLab Repo 的 CI/CD 環境變數：

在 GibLab 專案內選單進入 Settings -> CI/CD，展開 Variables 區塊，指定變數名稱（這邊範例是 `GCP_SERVICE_ACCOUNT`）並將前面取得的 JSON 檔案的內容貼進變數的值。

這邊要先手動方式在 Kubernetes 產生好 Deployment，GitLab CD 只透過 set image 指令更新 image 版本。

撰寫 .gitlab-ci.yaml 檔案，這邊實作兩個步驟：

1. 編譯 Docker Image 並上傳到 GCR（build-docker）
2. 透過 kubectl set image 方式更新 Deployment 的 image（deploy-k8s）

<pre>
stages:
  - build-docker
  - deploy-k8s

variables:
  GCP_GCR: asia.gcr.io/[[BUCKET_NAME]]/[[IMAGE_NAME]]

build_docker:
  image: "docker:18.09"
  services:
    - docker:18-dind
  stage: build-docker
  before_script:
    - apk -Uuv add curl bash python
    - curl https://sdk.cloud.google.com | CLOUDSDK_CORE_DISABLE_PROMPTS=1 bash
    - export PATH=$PATH:/root/google-cloud-sdk/bin/
    - echo $GCP_SERVICE_ACCOUNT > /root/key.json
    - gcloud auth activate-service-account --key-file /root/key.json
    - gcloud auth configure-docker --quiet
    - docker login -u _json_key --password-stdin https://asia.gcr.io < /root/key.json
  script:
    - docker build -t ${GCP_GCR}:${CI_COMMIT_SHA:0:8} .
    - docker push ${GCP_GCR}:${CI_COMMIT_SHA:0:8}

deploy-k8s-test:
  image: google/cloud-sdk:latest
  stage: deploy-k8s
  before_script:
    - echo $GCP_SERVICE_ACCOUNT > /root/$key.json
    - gcloud auth activate-service-account --key-file /root/key.json
    - gcloud container clusters get-credentials [[K8S_CLUSTER_NAME]] --zone asia-east2-c --project [[GCP_PROJECT_NAME]]
  script:
    - kubectl set image deployment app app=${GCP_GCR}:${CI_COMMIT_SHA:0:8} --record
  dependencies:
    - build_docker
</pre>

（記得自行替換掉 `BUCKET_NAME` 以及 `IMAGE_NAME` 甚至是 gcr.io 的 region）

接下來每次 commit 就會自動觸發 GitLab CI/CD，自動編譯出 Docker Image 並上傳到 GCR，然後自動 deploy 到 Kubernetes 上，完成整個持續建置與持續部署的動作。

-

參考：[Publishing Google Cloud Container Registry Images from Gitlab CI](https://medium.com/@gaforres/publishing-google-cloud-container-registry-images-from-gitlab-ci-23c45356ff0e)
