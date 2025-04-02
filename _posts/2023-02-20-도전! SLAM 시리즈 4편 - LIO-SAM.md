---
title: 도전! SLAM 시리즈 4편 - LIO-SAM
date: 2023-02-18 10:53:11 +9:00
categories: [Projects(Ko), SLAM]
tags: [SLAM, LIDAR, velodyne, LIO-SAM, liorf]
---

Ouster 라이다의 특징이 imu가 내장되어 있다는 것임을 들었기에, 다른 SLAM기법들 보다 IMU를 함께 사용하는 방식을 꼭 한번 해보고 싶다고 생각했었다.

그러던 중 LIO-SAM이 내가 원하는 요건에 잘 부합하는 것 같아서 도전해 보았다.

막상 하려고 하니 청천벽력 같은 소식.. LIO-SAM은 9DOF 이상의 IMU만 지원한다는 것이었다.

OS-1라이다의 내장 IMU는 6DOF….

그러던 중 해당 패키지를 6DOF IMU도 지원할 수 있도록 해놓은 리포지토리를 발견 다시 도전했다.

설치과정에 조금의 어려움이 있었지만, 실행시키는데 까지는 성공했다. 포인트클라우드가 rviz에 표시되는 걸 보고 신기해 하고 있을 무렵 정말로 신기한 일이 일어났다. rviz 상의 차량 위치좌표가 하늘을 향해 로켓처럼 치솟더니 동에번쩍 서에번쩍 하기 시작했다.

imu의 hz가 달라서 그런가… 싶어서 hz도 바꿔보고 토픽이 안나오고 있나 싶어서 rostopic list와 echo로 확인도 해보았는데 정상적으로 다 나오고 있었다. bag파일이 잘못되었나 해서 다른걸로 실행해 보아도 여전히 문제는 발생했다.

무언가 칼레브레이션을 해줘야 하나 싶은 생각도 해 보았지만, 라이다/카메라/레이더를 퓨전할때 처럼 정확한 거리데이터를 가져다 주는게 아닌데 패키지 내에서 제공하는 pre~~ 이상의 보정이 필요할까 싶었고, 다시 한참을 해메기 시작했다.

그러다가 처음에 잠깐 의심했던 좌표축을 다시 떠올렸다. 그때는 velodyne와 ouster의 0점? 기준이 달라서 그런가 라고 잠깐 생각했었으나 해당 패키지는 ouster를 지원한다고 올라와 있었기에 아니겠지 하고 넘어갔다.

그러나 곰곰히 생각하다 보니 위로 솟구치는게 z축 방향이 아니라 x축 방향이었으면 정상적으로 차가 직진하는건가….? 라는 생각이 들었고 extrinsicRot 옵션에서 값을 변경해보았다.

그리고 실행하니 정상적으로 잘 실행되었다.

근데 뭔가 센서를 추가했음에도 불구하고 크게 더 나은 점이 있다는 생각은 들지 않았다. 더 많은 상황과 더 많은 조건을 경험해 보아야 하겠지만.

<iframe width="560" height="315" src="https://www.youtube.com/embed/WdcWjyxrfmY?si=afKaP5h8uolaj4OW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>