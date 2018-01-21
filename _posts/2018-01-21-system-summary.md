---
layout: post
title: 시스템 개요
tags: [시스템, 개요]
---

![Image of system design]({{ site.baseurl }}/assets/img/pexels/system_design.png)

클라이언트는 안드로이드와 iOS로 개발이 되고, 공유 등의 기능을 위해 web이 지원되는 형태로 개발을 할 예정입니다.
서버는 전체적으로는 Google Cloud 서비스를 이용하여 개발을 할 예정입니다.

* Google App Engine : RESTful API(JSON) 및 웹퍼블리싱
* Google Cloud SQL : 사용자, 가게, 쿠폰 데이터 저장
* Google Cloud Storage : 사용자 프로필 사진 및 가게 사진 등 저장
* Google Firebase Cloud Message / APNs : 푸시 메시지 알림 전송
* Google Firebase 인증 : 사용자 회원가입 및 로그인
* Google Firebase 동적 링크 : 외부 웹페이지와 앱 호출 연동
* Google Firebase 애널리틱스 : 앱사용 통계

