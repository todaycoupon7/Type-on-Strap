---
layout: post
title: 바코드 생성기와 스캐너
tags: [barcode, 바코드, 생성기, 스캐너, zxing]
---

쿠폰 서비스에서 필수는 바코드 입니다. 편리하게 쿠폰을 발행하고 손쉽게 스캔을 통한 확인이 가능하기 때문입니다.

그래서, 이번엔 바코드 생성기와 스캐너를 구현 하였습니다.

안드로이드에서 바코드는 주로 zxing 라이브러리를 사용하여 개발합니다. 대부분의 서비스들이 zxing 소스를 레퍼런스하여 개발을 합니다.

금번 프로젝트에서도 zxing 소스를 튜닝하여 사용한다면 좀더 나은 서비스를 개발할수도 있겠지만, 개발 기간도 있겠지만 사용자에게 큰 불편함이 발생하는 부분이 아니기때문에 라이브러리를 그대로 사용하기로 합니다.

하지만, 그대로 사용하기엔 제가 생각한 스캐너 컨셉과는 다소 맞지 않는 부분이 있어, 이부분은 추가 개발을 진행하였습니다.


![Image of barcode scanner]({{ site.baseurl }}/assets/img/pexels/barcode_scan_gen.png)


라이브러리 사용은 소스 코드를 보거나, 구글링을 하시면 많이 나오기때문에 패스하고, 제가 수정한 부분에 대해서 설명드리겠습니다.

제가 개발하려는 컨셉은 스캐너 화면에서 계속(연속적으로) 스캔을 하는 기능입니다.

현재 라이브러리의 CaptureActivity를 상속받아 스캐너 화면을 구현하면 스캔 후 화면이 종료되게 됩니다.

따라서, 종료되지 않고 스캔 결과를 반환하면서, 임의의 시간(약1초)이 지난후에 다시 스캔 상태가 되도록 수정했습니다.


소스 코드의 ExtCaptureManager 클래스가 이 부분을 담당하는 것으로

    @Override
    protected void returnResult(BarcodeResult rawResult) {
        if(mListener != null) {
            mListener.onResult(rawResult.getText());
        }
        mHandler.postDelayed(mRefreshRunnable, REFRESH_INTERVAL);
    }
    
    private Runnable mRefreshRunnable = new Runnable() {
        @Override
        public void run() {
            mScannerView.resume();
            decode();
        }
    };

위의 코드와 같이 returnResult를 override해서 종료됨을 막고 결과를 받게 됩니다.

이후 임의의 시간(REFRESH_INTERVAL) 후에 mRefreshRunnable를 실행하여 다시 스캔 상태가 되도록 합니다.


자세한 내용은 Git의 [barcode-scan-with-generator](https://github.com/todaycoupon7/barcode-scan-with-generator) 소스코드를 참조하시면 될것 같습니다.


