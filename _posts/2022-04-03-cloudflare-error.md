---
layout: post
title: "클라우드플레어 ERR_SSL_VERSION_OR_CIPHER_MISMATCH 오류 해결하기"
tags: [web]
comments: true
---

클라우드플레어 이용 시 ERR_SSL_VERSION_OR_CIPHER_MISMATCH 오류가 발생했을 떄 해결하는 방법입니다

---

클라우드플레어 서비스 이용 시 ERR_SSL_VERSION_OR_CIPHER_MISMATCH 오류가 발생했을 떄 해결하는 방법입니다

## 해결
- 서브도메인 사용하지 않기
  
  서브도메인 사용 시 클라우드플레어 무료 플랜에서는 프록싱과 https를 지원하지 않는 것으로 보입니다
  
- http로 들어가기
  
  `항상 https 사용` 옵션을 꺼두면 http로도 사이트에 들어갈 수 있는데 그렇게 된다면 해당 오류가 발생하지 않습니다

- 돈내기

  SSL/TLS -> 고급 인증서 주문에 있는 월 10달러짜리 고급 인증서 관리자 플랜을 사게 된다면 오류가 발생하지 않는다는 말을 검색 중 보았지만 실제로 테스트해보지는 않아 장담할 수 없습니다


---

저같은 경우에는 서브도메인(.)이 아닌 하이픈(-)으로 바꾸어서 해결했습니다
