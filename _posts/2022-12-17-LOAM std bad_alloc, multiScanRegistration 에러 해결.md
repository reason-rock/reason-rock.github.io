---
title: LOAM std bad_alloc, multiScanRegistration 에러 해결
date: 2022-12-17 10:53:11 +9:00
categories: [Linux, (Ko)]
tags: [std::bad_alloc, PCL, SLAM, loam, multiScanRegistration]
---

PCL을 가지고 수도 없이 삽질을 하던 끝에 어찌어찌 해결을 보고,대안으로 진행중이던 새로운 센서 연동이고 뭐고 일단 다 미뤄두고 본격적으로 라이다로 할 수 있는 것들에 집중하여 경험해보고자 완성된 패키지를 구동해보는 것으로 방향성을 틀어보려 했다.

그래서 예전부터 해보고 싶었던 라이다 SLAM을 위해 여기저기 검색해보니 loam이 그나마 다가가기 쉬워 보였고, 설치 하고 실행해보았다.

다 짜놓은 코드 그냥 설치해서 빌드만 하면 되니 에러는 없겠지..... 라는 기대를 품고 돌려봤으나

어림도 없지 ㅋㅋ

```
terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
[multiScanRegistration-2] process has died [pid 9926, exit code -11, cmd /home/reason_rock/loam_Ws/devel/lib/loam_velodyne/multiScanRegistration /multi_scan_points:=/velodyne_points __name:=multiScanRegistration __log:=/home/reason_rock/.ros/log/337aff0e-7ebd-11ed-b4f4-6146aee6e92f/multiScanRegistration-2.log].
log file: /home/reason_rock/.ros/log/337aff0e-7ebd-11ed-b4f4-6146aee6e92f/multiScanRegistration-2*.log
```
에러가 떴다.

다행히도(?)이 문제는 공식 깃허브 리포지토리에 Trouble shooting 항목에 정의되어 있는 문제였다.

공식 문서에서 제시하는 해결책은 간단하다.

Cmake list 35번째 줄
add_definitions( -march=native )

을 주석처리 후 빌드

그럼에도 불구하고, 잘 되지 아니했다.

그래서 또 이래저래 서칭을 해보니 컴파일시 C++ 버전을 바꿔보라, PATH 지정을 해봐라, 뭐를 추가해라 뭐를 빼라 하라는 모든 것을 다 해봤다.

그랬음에도 불구, 잘 되지 않자 결국 마음속으로 부정하고, 또 부정했던 해결책 밖에 남지 않았다.

1. 바로 ros noetic에서 문제가 좀 많이 생기더라, dashing으로 버전을 내려라.....
2. 그게 아니면 PCL이 문제라는 것이었다. 젠장할.... PCL로 몇날며칠을 고생하고 겨우 한가지 문제를 해결해서 안도한게 엊그제였는데, PCL은 오늘도 내 발목을 거하게 잡으신다.

그래서 포맷을 하려다 똑같이 설정해두던 다른 노트북에 깔고 돌려보았다.

여전히 해당 에러가 발생하였고, 그럼 그렇지 라는 생각으로 cmake 주석처리 후 빌드했는데

얼레? 돌아간다. 일단 저건 안뜨더라.

물론 뭔가 이상하긴 마찬가지였다.

Fixed frame의 camera_init은 에러를 뿜어냈고 포인트클라우드와 imu는 보이지도 않는데 그냥 좌표계 원점만 허공으로 날라다니고 있었다.

그러나 에러 메세지를 보니 간단히 해결할 수 있었다.

그냥 에러처럼 경로를 맞춰 /를 하나 추가해주니 정상적으로 실행되었다.

이런 젠장할.

결국에는 내 컴퓨터가 문제였던 것이었다.

2주간의 라이다/PCL 삽질기는 이렇게 다른 국면을 맞게 되었다.

