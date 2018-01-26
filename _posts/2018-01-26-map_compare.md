---
layout: post
title: Daum 지도와 Naver 지도 서비스 비교
feature-img: "assets/img/pexels/map_and_child.jpg"
tags: [daum지도, naver지도, staticMap]
---

쿠폰을 사용 할수 있는 가게를 표시하기 위해 지도 서비스는 필수 요소입니다.

현재 국내에 서비스 중인 대표 지도 서비스인 Daum 지도와 Naver지도를 비교해 보았습니다. (Google 지도의 경우엔, 최근 1~2년 사이에 개발된 지역(신도시 등)에 대해서는 업데이트가 되어있지 않아 제외 했습니다.)

먼저, 오늘쿠폰 서비스에서 지도 서비스는 화면 전체의 지도 위에 쿠폰 서비스 중인 가게의 위치를 표시(marker)하고, 이를 클릭시에 해당 가게의 상세화면으로 진입하여 상세정보와 함께 지도 이미지에 해당 가게의 위치를 간략하게 표시하는 것으로 기획했습니다.

처음엔 간단하게 각각의 화면에 지도를 표시하는 것을 생각했지만, 실제 구현해 보니 하나의 앱에서는 하나의 지도 인스턴스만을 사용 할수 있었습니다.(Activity1에서 지도를 표시하고 다른 Activity2로 이동하여 지도를 사용하려면 Activity1의 onPause()시에 인스턴스를 해제하고 Activity2에서 인스턴스를 다시 받아서 사용되어야 합니다.)

그래서, 다시 구글링을 통해서 static Map 이미지를 사용하면 되는 것을 확인하였습니다. static Map 이미지는 서버에 지도 이미지 요청 URL을 만들어서 요청하면 해당 부분의 이미지를 반환해주는 것으로 오늘쿠폰 서비스의 기획의도와 일치한다고 볼 수 있습니다.

## Daum 지도
![Image of daum map]({{ site.baseurl }}/assets/img/pexels/daum_map.png)

[Daum 지도 API](http://apis.map.daum.net/) 사이트를 보면, 굉장히 쉽고 간단하게 지도를 사용할수 있도록 되어있어 짧은 시간에 개발을 할 수 있었습니다. 그런데, static Map을 사용하려면 Javascript를 사용하여야 하는 이슈가 있었습니다. 아~~~~~~ㅠㅠ

다시 이것 저것 해보면서 궁리를 하던중에 Javascript를 통해서 표시된 이미지의 URL의 parameter값을 변경해도 원하는 결과를 얻을 수 있다는 것을 확인하여 static Map 이미지를 구현 하였습니다.

```
http://map2.daum.net/map/imageservice?IW={WIDTH}&IH={HEIGHT}&MX={WCONG_X}&MY={WCONG_Y}&SCALE=2.5&COORDSTM=WCONGNAMUL
```

그런데, 이번엔 static Map 화면으로 이동했다가 다시 지도 화면으로 돌아오면 daum 지도에서 화면을 refresh 합니다. 이건 여러가지 보았지만 수정을 못했습니다. (혹시, 수정 방법을 아시는 분은 연락 부탁드려요..^^)

## Naver 지도
![Image of naver map]({{ site.baseurl }}/assets/img/pexels/naver_map.png)

[Naver 지도](https://developers.naver.com/products/map/) 사이트와 [Sample project](https://github.com/navermaps/maps.android) 를 참고하여 개발하였습니다. Daum 지도에 비해서는 봐야 할 부분이 많고, 다소 복잡한 부분이 있었습니다.

static Map 이미지 사용은 Naver에 Application 등록시에 '지도 (웹)' 을 설정해야 사용할 수 있습니다. 설정시에 WEB URL을 입력하도록 되어 있는데 임의의 URL을 입력하여 사용하여도 무방한 듯 합니다.)

static Map의 가이드는 Naver 지도 > 튜토리얼 > static Map 지도 시작하기 탭을 보시면 상세하게 가이드되어 있습니다.

```
https://openapi.naver.com/v1/map/staticmap.bin?clientId={CLIENT_ID}&url={Application에 등록한 WEB URL}&crs=EPSG:4326&center={LONGITUDE},{LATITUDE}&level=13&w={WIDTH}&h={HEIGHT}&baselayer=default
```

## 결론
개발의 편리성과 속도면에서 Daum 지도가 큰 점수를 줄 수 있을것 같지만, 화면 이동 후에 지도가 refresh가 되는 것은 다소 문제가 있어 보입니다. 반면에 Naver 지도는 개발의 불편함(?)과 좀더 연구가 필요한 부분에 있어서 조금 고민을 하게 됩니다.

본 글의 지도를 검토한 소스 코드는 [Multi-Activity-with-KakaoMap](https://github.com/todaycoupon7/Multi-Activity-with-KakaoMap) 에 업로드 하였습니다. 궁금하신 분은 참고하시면 좋을 것 같습니다.^^
