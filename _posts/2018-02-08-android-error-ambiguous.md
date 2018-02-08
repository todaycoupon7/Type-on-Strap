---
layout: post
title: Ambiguous method call. Both findViewById(int) in AppCompatActivity and findViewById(int) in Activity match
tags: [android, error, ambiguous, method, call, findViewById]
---

업무상 필요해서 예전 이클립스에서 개발되었던 프로젝트를 Android Studio 로 import를 진행하였습니다. 몇가지 문제가 되는 부분들 수정하면서 무사히 import도 완료하고 업무도 잘 처리했었습니다.

그런데, 이후에 기존에 Android Studio에서 개발중이던 프로젝트에서 아래와 같은 에러가 발생하더라구요.. 헐~!


![android-error-ambiguous]({{ site.baseurl }}/assets/img/pexels/android-error-ambiguous.png)


$$$ Ambiguous method call. Both findViewById(int) in AppCompatActivity and findViewById(int) in Activity match $$$


에러 메시지로 구글링도 해서 이것저것 해보지만 해결이 되지 않았습니다.

그러던중에 우연히(?) 해결이 되었습니다.

그것은 build.gradle 에 임의의 수정(지웠다가 다시 붙었다.. 등등) 으로 다시 sync를 하게 되면 에러가 사라지고 이슈가 해결이 됩니다.

혹시 위의 같은 이슈가 있으신 분은 한번 해보시길 권해드립니다. ^^ㅎ
