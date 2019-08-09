---
title: "Run SmokePing by Nginx with FastCGI"
date: 2019-08-08T01:56:23+08:00
thumbnail: "images/2019-08-09-SmokePing-Nginx-CGI.png"
tags: ["nginx", "smokeping"]
description: "將 SmokePing 透過 FastCGI 跑在 Nginx 上"
---

SmokePing 是一個網路品質監控的 open source 軟體，可以用來持續監控伺服器到各個網路節點、服務等的網路狀況。SmokePing 主要使用 Perl 撰寫，除了背景有個 daemon 會一直到各個 Targets 去蒐集網路連線狀態外，也有個簡單的 Web 可以看圖表，由於是 Perl 寫的，需要透過 CGI 的方式讓 web server 去讀，這在 Apache 上很容易，但如果是要用 Nginx 來做為 web server，需要透過 spawn-fcgi 來實現（與 Nginx + PHP 的方式類似）。

主要測試的環境為 Ubuntu/Debian Linux，首先安裝 Nginx、SmokePing 以及 Spawn-FCGI 這三個套件。

    apt install nginx smokeping spawn-fcgi

建立 Systemd 服務設定檔案 `/etc/systemd/system/smokeping-fcgi.service` 放入下列內容：

```
[Unit]
Description=SmokePing FastCGI Service
After=network.target smokeping.service
Wants=smokeping.service

[Service]
StandardOutput=null
StandardError=syslog
ExecStart=/usr/bin/spawn-fcgi -u smokeping -s /run/smokeping-fcgi.sock -M 600 -n -U www-data -- /usr/share/smokeping/smokeping.cgi
Restart=always

[Install]
WantedBy=multi-user.target
```

透過指令啟用 SmokePing FastCGI Service：

```
systemctl daemon-reload
systemctl enable smokeping-fcgi
systemctl start smokeping-fcgi
```

在 Nginx 設定中放入 SmokePing 預計所在的網址：

```
location = /smokeping/ {
    fastcgi_pass unix:/run/smokeping-fcgi.sock;
    include /etc/nginx/fastcgi_params;
}

location /smokeping/ {
    alias /usr/share/smokeping/www/;
}
```

重啟 Nginx：

    systemctl reload nginx.service

用瀏覽器打開網址 http://localhost/smokeping/ ，如果採用預設值，大約要等 10 分鐘後，即可在畫面上看到監測數據慢慢出現。
