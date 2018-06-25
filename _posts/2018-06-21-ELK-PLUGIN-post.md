---
layout: post
title: "ELK Plugin 적용방법"
tags: [code, elk, plugin]
---

#ELK Plugin 적용 방법

## X-PACK(사용자 인증) plugin 적용하기

### 1. elasticsearch 플러그인 install

```
/usr/share/elasticsearch/bin/elasticsearch-plugin install x-pack
```

* plugin 명령어 옵션 (list, install, remove)

### 2. kibana 플러그인 install

```
/usr/share/kibana/bin/kibana-plugin install x-pack
```

* kibana 플러그인 까지 설치완료 되면 elasticsearch의 user와 password를 설정하자

### 3. logstash 설정 변경

```
output {
    elasticsearch {
      hosts => ["127.0.0.1:9200"]
      user => "유저아이디"
      password => "비밀번호"
    }
```

* elasticsearch 의 user와 password를 설정해준다.
