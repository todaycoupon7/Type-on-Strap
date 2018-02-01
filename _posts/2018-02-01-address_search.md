---
layout: post
title: 다음(Kakao) 로컬 API를 이용한 주소 검색 (feat. 자동완성)
tags: [daum, 다음, kakao, 카카오, 로컬api, 주소, 검색, 자동완성]
---

오늘쿠폰 서비스는 가게에서 쿠폰을 발행해야 하는 서비스이기때문에 가게의 위치가 필수 사항이라고 할수 있습니다. 가게에서 손쉽게 가게의 주소를 등록할 수 있는 기능을 만들어 보도록 하겠습니다.


필요한 기능은 가게 등록시 주소 키워드를 입력하면 키워드에 해당하는 주소 목록을 가져와서 선택하면 좋을 것 같습니다. 추가적으로 주소 키워드 입력시에 자동완성 목록도 보여주면 더욱 세련되어 보일것 같습니다.

다음 지도 서비스를 이용할 예정이므로 주소 검색 기능도 다음(Kakao)의 로컬 API를 이용하기로 하였고, 자동완성 기능은... 음......... 어디 지원해주는 곳이 없는지 기웃~기웃~ 거려봅니다만.. 없습니다..;;;;

없으면 찾아내면 됩니다..ㅎ;;; 다음의 [우편번호 서비스](http://postcode.map.daum.net/guide)에서 주소 키워드 입력시에 자동완성 목록이 표시됩니다. 올타쿠나!!^^ 크롬의 개발자 도구를 이용하여 호출 URL을 얻어내어 요리조리 사용해보니 json 데이터가 내려오는 것을 확인합니다. 이걸로 구현 합니다.


![image of address search]({{ site.baseurl }}/assets/img/pexels/address-search.png)


짜잔~! 완성했습니다.


해당 소스는 [https://github.com/todaycoupon7/search-address-with-autocomplete](https://github.com/todaycoupon7/search-address-with-autocomplete) 에 올려놓았으니 관심있으신 분은 보셔도 좋을 것 같습니다.

