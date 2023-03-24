# Elk Stack with Redis

## Feature

- Elk Stack 과 Redis Proxy를 통해 종단 서비스의 로그를 수집 관제할 수 있는 Monitoring Server의 Docker 구축 프로세스

## Stack

- Elasticsearch
- Logstash
- Kibana
- Redis
- Filebeat
- Docker (with docker-compose)

## Installation

1. Elk Stack의 초기 구성에 사용할 Built-In User들의 비밀번호와 서비스의 버전에 대한 정의를 원하는 환경으로 수정

```sh
cd elk-server
vi .env
```

2. Docker-Compose 를 이용해 해당 구성을 실행

```sh
docker compose up -d
```

## Configuration

1. Linux Configuration

- vm.max_map_count 커널 셋팅은 최소 262144 이상

```sh
    grep vm.max_map_count /etc/sysctl.conf
    vm.max_map_count=262144
```

## Notify

1. Built-In User "kibana_system" 의 초기 권한은 Kibana UI 에 대한 접근권한이 허용되어 있지 않으므로 Kibana UI 에 관리자 로그인을 하기 위해서는 Built-In User "elastic" 으로 로그인 해야 접근할 수 있다.

## Reference

- https://www.elastic.co/guide/index.html
- https://github.com/deviantony/docker-elk
