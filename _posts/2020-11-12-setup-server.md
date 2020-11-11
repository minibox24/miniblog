---
layout: post
title: "우분투에 파이썬, C#, nodejs, mongodb 설치"
tags: [ubuntu]
comments: true
---

우분투 18.04+에 파이썬 3.9와 Dotnet 런타임 3.1과 nvm을 통한 nodejs, mongodb를 설치해봅시다.

---
우분투 18.04+에 파이썬 3.9와 Dotnet 런타임 3.1과 nvm을 통한 nodejs, mongodb를 설치해봅시다.

(사실 그냥 메모)

## NodeJS
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.0/install.sh | bash
# ssh 재접속
nvm install --lts
```
\+ pm2 설치 `npm install pm2 -g`

## Python
```bash
# 빌드 툴 설치
sudo apt install build-essential checkinstall libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev libffi-dev zlib1g-dev -y

# 다운로드
cd /opt
sudo wget https://www.python.org/ftp/python/3.9.0/Python-3.9.0.tgz
sudo tar xzf Python-3.9.0.tgz

# 설치
cd Python-3.9.0
sudo ./configure --enable-optimizations
sudo make altinstall

# path 설정
update-alternatives --install /usr/bin/python python /usr/local/bin/python3.9 1
update-alternatives --install /usr/bin/pip pip /usr/local/bin/pip3.9 1
```

## Dotnet
```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
sudo apt update
sudo apt install -y dotnet-runtime-3.1
```

## mongodb
```bash
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
sudo apt-get update
sudo apt-get install -y mongodb-org
```
