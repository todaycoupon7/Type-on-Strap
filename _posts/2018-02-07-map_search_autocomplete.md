---
layout: post
title: 네이버 지도 검색시 자동완성 URL 이용하기
tags: [naver, 네이버, 지도, map, 자동완성, autocomplete]
---

지도에서 검색을 하기 위해 키워드를 입력하는데, 이때 자동키워드 제안이 되어 자동완성 기능이 되면 좀더 스마트한 기능이 되기때문에 이를 구현하는 방법을 소개 드립니다.

공식적으로 자동 키워드 제안 API는 구글 정도만 지원해주고, 다른 곳에서는 (무료로)지원해주는 곳을 알지못합니다.

구글 API도 좋지만, 지도 서비스를 하기때문에 실제 지도 서비스의 자동 키워드 제안이 좀더 나을 것 같다는 생각으로 네이버 지도의 자동 키워드 제안의 URL을 이용하기로 합니다.


![naver_map_auto_suggest]({{ site.baseurl }}/assets/img/pexels/map_search_autocomplete_1.png)


위의 이미지와 같이 네이버 지도에서 자동 키워드 기능을 제공을 하고 있습니다. 텍스트 입력시에 자동 키워드 제안 호출 URL을 알수 있다면 이용할 수 있을 것 같다는 생각이 듭니다.


크롬 브라우저에서 (네이버 지도)[https://map.naver.com/] 사이트로 이동합니다.

[보기] - [개발자 정보] - [개발자 도구] 를 선택하면 아래와 같은 화면을 확인하실수 있습니다.


![chrome_dev]({{ site.baseurl }}/assets/img/pexels/map_search_autocomplete_2.png)


이제 네이버 지도 검색창에 검색어를 입력합니다. 저는 "맛" 이라고 입력했습니다.
그렇게하니 오른쪽 화면에 추가로 뭐가가 생깁니다. 해당 항목을 클릭해보면 바로 호출 URL입니다.

General 항목에 Request URL 부분을 보면 URL을 확인할 수 있습니다.

이 URL을 복사하여 크롬의 주소 입력창에 넣어보면서 requst parameters 를 조정하면서 최적을 URL을 찾아내면 됩니다.


이와같이하여 자동완성 기능을 구현할 수 있는 URL을 얻었으니, android를 앱을 만들어 보았습니다.


![android_sample_app]({{ site.baseurl }}/assets/img/pexels/map_search_autocomplete_3.png)


위의 이미지를 보시면, 네이버 지도에서 나왔던 제안된 키워드 내용이 동일함을 확인하실 수 있습니다.


안드로이드 앱은 github((map_search_autocomplete)[https://github.com/todaycoupon7/map_search_autocomplete])에 올려놓았으니 참고하시 분은 보시면 좋을 것 같습니다.

