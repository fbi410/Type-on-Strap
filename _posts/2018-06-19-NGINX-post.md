---
layout: post
title: "NGINX CONFIGURATION"
tags: [code, nginx]
---

#Nginx Configuration

## 1. Listen Port
* 기본 포트는 80

```
server {
  listen   80;
  ....
}
```

## 2. Document Root
* 기본 디렉토리는 html

```
location / {
  root html;
}
```

## 3. 초기 페이지

```
location / {
  index index.html;
}
```

## 4. proxy_pass
* 특정확장자 (.do) 로 들어오는 요청을 http://localhost:8080 으로 넘기는 설정

```
location ~ \.do$ {
  proxy_pass http://localhost:8080;
}
```

## 5. Sub Domain
* 하나의 서버에서 여러 도메인을 사용할 경우

```
server {
        listen       80;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
            root   /home/nginx;
            index  index.html index.htm;
        }
        ......
    }

    server {
        listen       80;
        server_name  nginx1.com;

        location / {
            root   /home/nginx1;
            index  index.html index.htm;
        }
    }

    server {
        listen       80;
        server_name  nginx2.com;

        location / {
            root   /home/nginx2;
            index  index.html index.htm;
        }
    }
```

## 6. access log
* sub domain 별로 access log를 따로 쌓고 싶은 경우 개별로 설정을 해주어야 함

```
server {
        listen       80;
        server_name  localhost;

        #charset koi8-r;

        access_log  logs/host.access.log;
        ......
    }    

    server {
        #listen       80;
        server_name  nginx1.appsroot.com;

        access_log  logs/nginx1.access.log;
        ......
    }

    server {
        #listen       80;
        server_name  nginx2.appsroot.com;

        access_log  logs/nginx2.access.log;
        ......
    }
```
