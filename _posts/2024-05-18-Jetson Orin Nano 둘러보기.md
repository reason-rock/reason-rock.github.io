---
title: Jetson Orin Nano 둘러보기
date: 2024-05-18 20:53:11 +9:00
categories: [Device Overview, Embedded]
tags: [NVIDIA, ORIN, Jetson Nano, Jetson Orin Nano, 엔비디아, 젯슨, 젯슨나노, 오린]
---

기존까지 Jetson Nano로 테스트하던 프로젝트를 본격적으로 진행하게 되며 Jetson Orin Nano을 사용해 볼 기회가 생겼다.


![Orin_1](https://github.com/reason-rock/reason-rock.github.io/assets/98293904/84b6f977-f324-4b12-af06-8764c01067f9)


Orin nano는 기존 Jetson nano 시리즈의 후속작 개념으로, Ampere 아키텍쳐를 사용하는 Orin 시리즈의 일종이다.

다만 기존 Maxwell 아키텍쳐의 제품 대비 엄청난 가격인상(30만원대 → 80만원대(8GB기준))으로 선뜻 구매하기에는 손이 잘 안가는 가격을 자랑한다.

개선점으로는 우선 성능은 Maxwell GPU  + ARM A57 CPU에서 Ampere GPU와 Arm Cortex-A78AE CPU로 개선되었고 메모리 또한 LPDDR4에서 LPDDR5로 개선되었다고 하나, 실질적으로 체감할 정도의 작업은 아직 해보지 않았기에 크게 와닿지는 않았다.


![Orin_2](https://github.com/reason-rock/reason-rock.github.io/assets/98293904/364f8024-0275-4065-bae1-d0e3d8122f7e)

개인적으로 눈에 띄는 차이는 마이크로 SD나 USB 부팅을 해야했던 기존 젯슨나노 대비 SSD 장착이 가능한 포트가 추가되었다는 점, 팬이 내장되었다는 점, 5핀 대신 C타입으로 전원을 받을 수 있다는 점, 쌩 기판이 아닌 플라스틱 플레이트가 추가되었다는 점 등이 있다.

하지만 단점은 
HDMI 포트가 사라지고 영상출력은 DP포트를 통해서만 가능하다는 점(AGX Orin과 동일), C타입은 영상출력을 지원하지 않는다는 점, 플라스틱 플레이트가 추가되었지만 하부 기판을 완전히 커버하는 것은 아니라는 점(이는 SSD 장착 포트가 하단부에 있기에 어쩔 수 없는 부분이긴 하다.)

그리고 여전히 이해가 가지 않는 19볼트 어댑터…. 9~20V 정도의 전압 입력이 가능해서 12V를 꽂아 쓰면 되지만 굳이 왜 기본으로 19볼트를 사용하는지는 의문. 노트북 전원과의 호환을 위한건지.. 12V나 효율성 측면에서 별 차이가 없을텐데 19v 어댑터를 주는 바람에 괜히 어댑터의 종류만 많아진다.