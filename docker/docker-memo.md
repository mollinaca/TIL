
# docker自体のインストール

## 公式的なやつ

https://docs.docker.com/install/linux/docker-ce/centos/
https://qiita.com/ymasaoka/items/b6c3ffea060bcd237478
https://qiita.com/inakadegaebal/items/be9fecce813cebec5986

## 特にこだわりなければなんでもいいと思う

CentOS7/AmazonLlinux なら以下のみでとりあえず平気(AWS EC2)
```
# cat /etc/*-release
NAME="Amazon Linux"
VERSION="2"
ID="amzn"
ID_LIKE="centos rhel fedora"
VERSION_ID="2"
PRETTY_NAME="Amazon Linux 2"
ANSI_COLOR="0;33"
CPE_NAME="cpe:2.3:o:amazon:amazon_linux:2"
HOME_URL="https://amazonlinux.com/"
Amazon Linux release 2 (Karoo)
```

```
$ yum install docker
 => docker-18.06.1ce-10.amzn2.x86_64
```

# docker-compose

https://qiita.com/uhooi/items/fb14d99d3323bd2eee9d

```
$ curl -L https://github.com/docker/compose/releases/download/1.24.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
$ chmod +x /usr/local/bin/docker-compose
```

# python3

https://qiita.com/reflet/items/4b3f91661a54ec70a7dc
python3 の実行環境専用docker

```
# pwd
/root/docker/python3
```

* Dockerfile
```
FROM python:3
USER root

RUN apt-get update
RUN apt-get -y install locales && \
    localedef -f UTF-8 -i ja_JP ja_JP.UTF-8
ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL ja_JP.UTF-8
ENV TZ JST-9
ENV TERM xterm

RUN apt-get install -y vim less
RUN pip install --upgrade pip
RUN pip install --upgrade setuptools
```

* docker-compose.yml
```
version: '3'
services:
  python3:
    restart: always
    build: .
    container_name: 'python3'
    working_dir: '/root/docker/python3/'
    tty: true
    volumes:
      - ./opt:/root/opt
```

* exec.sh
```
#!/bin/bash
docker-compose exec python3 bash
```
 → docker コンテナにログインする
 