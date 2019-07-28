---
title: "Clair"
date: 2019-07-24T11:05:04+08:00
draft: true
thumbnail: "images/2019-07-24-clair.jpg"
tags: ["devops", "clair", "docker"]
description: ""
---

[Clair](https://github.com/coreos/clair) 是一套針對容器 (Container) 進行弱點掃描靜態分析的開源工具，由 CoreOS 提供。

建立需要的目錄

```
mkdir -p clair-data/clair-config
```

Clair 所需設定檔（參考 https://raw.githubusercontent.com/coreos/clair/master/config.yaml.sample 進行修改），放在 `clair-data/clair-config` 目錄內，檔名 `config.yml`

```
clair:
  database:
    type: pgsql
    options:
      source: host=postgres port=5432 user=clair sslmode=disable statement_timeout=60000
      cachesize: 16384

  api:
    addr: "0.0.0.0:6060"
    healthaddr: "0.0.0.0:6061"
    timeout: 900s

  updater:
    interval: 2h
    enabledupdaters: 
      - debian
      - ubuntu
      - rhel
      - oracle
      - alpine
      - suse
```


`docker-compose.yaml` 檔案：

```
version: '2.1'

services:
  postgres:
    image: postgres:9.6
    restart: unless-stopped
    volumes:
      - ./clair-data/postgres-data/:/var/lib/postgresql/data:rw
    environment:
      - POSTGRES_PASSWORD=
      - POSTGRES_USER=clair
      - POSTGRES_DB=clair
    
  clair:
    image: quay.io/coreos/clair:v2.0.6
    restart: unless-stopped
    volumes:
      - ./clair-data/clair-config/:/config/:ro
      - ./clair-data/clair-tmp/:/tmp/:rw
    depends_on: 
      postgres:
        condition: service_started
    command: [--log-level=debug, --config, /config/config.yml]
    user: root

  clairctl:
    image: jgsqware/clairctl:latest
    restart: unless-stopped
    environment: 
      - DOCKER_API_VERSION=1.24
    volumes:
      - ./clair-data/clairctl-reports/:/reports/:rw
      - /var/run/docker.sock:/var/run/docker.sock:ro
    depends_on: 
      clair: 
        condition: service_started
    user: root
```

啟動 Clair

    docker-compose -f docker-compose-clair.yml up -d

分析 Docker Image

    docker-compose -f docker-compose-clair.yml exec clairctl clairctl report -l mongo:latest

取得報表檔案

    clair-data/clairctl-reports/html/
