---
layout: post
title: "클라우드 컴퓨팅 서비스에서 SSH 비밀번호로 로그인하기"
tags: [linux]
comments: true
---

클라우드 컴퓨팅 서비스에서 SSH 비밀번호로 로그인을 할 수 있도록 설정해봅시다.

---
GCP, AWS, Azure 등등의 클라우드 컴퓨팅 서비스에는 대부분 보안을 위해서 비밀번호로 로그인하는 것을 막아두었습니다.

하지만 보안 신경 쓰지 않고 비밀번호로 로그인 하겠다 하시는 분들은 밑 내용을 참고해서 비밀번호로 SSH 로그인하기를 활성화해보세요.

## 비밀번호로 로그인 활성화

```bash
sudo nano /etc/ssh/sshd_config
```

파일에 들어간 후 `PasswordAuthentication`항목을 `yes`로 변경해주세요.

## root 계정 로그인 활성화

또한 나는 보안따위 개나 줘버렸다 하시는 분들은 root 계정도 활성화하실 수 있습니다.

`sudo passwd` 명령으로 root계정의 비밀번호를 설정하신 후,
아까와 같은 파일에서 `PermitRootLogin`항목을 `yes`로 변경해주세요.

## 사용한 스크립트들

```bash
sudo passwd                                  // root 계정 비밀번호 설정
sudo nano /etc/ssh/sshd_config               // 설정 파일 열기


PermitRootLogin yes                          // root 로그인 허용
PasswordAuthentication yes                   // 비밀번호로 로그인 허용
```
