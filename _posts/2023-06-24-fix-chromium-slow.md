---
layout: post
title: "크롬 초기 렉 없애기"
tags: [windows, chromium, startup, idle, lag, slow, v8, electron, 20s, 20sec]
comments: true
---

크로미움 기반 브라우저나 일렉트론 앱에서 대략 20초동안 프로그램이 시작되지 않는 문제를 해결하는 방법

---

크로미움 기반 브라우저나 일렉트론 앱에서 대략 20초동안 프로그램이 시작되지 않는 문제를 해결하는 방법

https://github.com/minibox24/miniblog/assets/61264156/b36bd1af-65b8-459e-b69c-670a17112de8

Before

이따구로 크롬을 켜거나

![image](https://github.com/minibox24/miniblog/assets/61264156/07f72698-5b83-4788-9c5f-42d8a9c49507)

그냥 일렉트론 프로그램을 실행할때도 (디스코드도 해당됨)
23초 후에 프로그램이 드디어 로드되더라고요

일렉트론 main 프로세스를 보니까 그냥 idle 상태던데 ㅋㅋ

![image](https://github.com/minibox24/miniblog/assets/61264156/38be7e25-5dd1-4731-b6f2-0d870b515e92)

이거 끄시면 됩니다

![image](https://github.com/minibox24/miniblog/assets/61264156/dcc76425-f126-4dcc-bb6b-1852a181a30b)
![image](https://github.com/minibox24/miniblog/assets/61264156/e592ed4a-52da-4e40-aa44-38855af96b4e)




https://github.com/minibox24/miniblog/assets/61264156/2b93d8be-70fb-4217-81a3-e7e70acf430d

After



누군가가 이 태그로 찾아 들어오기를 바라며..
chromium startup idle lag slow v8 electron 20s 20sec
