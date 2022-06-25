---
title: Home Assistant를 위한 DIY 허브 만들기
date: 2022-06-10 10:53:11   
categories: [Projects(Ko), IoT(Ko)]
tags: [3D프린팅, 3D모델링, Iot, HA, Home Assistant, 네스트 허브, 홈어시스턴트]
---
HA를 구축하고 구글홈 음성인식까지 연동하였으나 직관적인 제어는 역시 터치가 편하다는 것을 느끼고, 네스트 허브를 살지 말지 고민하다 직접 만들어보기로 했다.<br>

<h3>준비물</h3>
 - 서랍에 굴러다니는 공기계<br>
 - 3년 묵은 3D프린터 필라멘트<br>
 - 약간의 모델링 능력<br>
 - 이미 구축된 HA 서버<br>
 - 커넥터가 망가진 케이블 일체형 스마트폰 충전기
 

<h4>STEP1. 스마트폰 환경 구성</h4>
1. 스마트폰에 최신 OS 설치(선택사항)<br>
이번 개조의 희생양을 베가넘버6로 잡았기에, 안드로이드 4.4.2를 최소 7이상으로 올려야 HA 공식 앱을 설치 할 수 있었다.(물론 그냥 웹으로 구동해도 상관없다.)<br>
<img src="/assets/img/VN6/VN6_2.jpg" width="200"><img src="/assets/img/VN6/VN6_11.jpg" width="200"><br>
자세한 과정은 별도의 글로 다룰 예정<br>
2. 스마트폰 상시전원 개조(선택사항)(탈착식 스마폰에만 권장)<br>
이 또한 노후된 기기이므로 애초에 배터리 상태가 좋지않아, 스웰링 방지를 위해 배터리를 제거하기로 결정했다.(물론 충전기를 상시로 연결해놓아도 상관없다)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. 배터리 분리 후 셀과 BMS 분리<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. BMS에 극성을 맞춰 5V 충전기 납땜<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3. 셀의 빈 공간을 채워 BMS가 본체 접점에 잘 맞물리도록 배치<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="/assets/img/HA_HUB/HA_HUB_2.jpg" width="200"><img src="/assets/img/HA_HUB/HA_HUB_1.jpg" width="200"><br>
3. HA 공식 앱 설치<br>


<h4>STEP2. 허브 프레임 설계</h4>
1. 먼저 사용하려는 휴대폰을 대략적으로 모델링해서 대략적인 형상을 잡는다.
2. 최대한 허브와 비슷한 형상을 내기 위해 배젤을 가리고, 액정만 보이면서 45도 각도로 사용성을 극대화하기 위해 노력했다.<br>
☆유의사항: 전원과 볼륨키를 위한 공간을 확보해야 함을 유의하라. 그렇지 않으면 출력후 장착했을때 이유없이 전원이 꺼지는 걸 보고 애꿎은 충전기와 땜질 탓을 하며 허송세월을 보내고, 소중한 출력물 하나를 버리게 될 것이다.<br>
<img src="/assets/img/HA_HUB/HA_HUB_5.jpg" width="200"><img src="/assets/img/HA_HUB/HA_HUB_6.jpg" width="200"><br>

<h4>STEP3. 출력 및 장착</h4>
1. 앞에서 만든 스마트폰과 허브 프레임을 결합하면 간단한 허브 만들기는 이렇게 끝이 난다.<br><br>
<img src="/assets/img/HA_HUB/HA_HUB_7.jpg" width="300"><br>
2. 이제 HA에 접속하여 허브를 위한 대시보드를 새로 만들어 커스터마이징 해주면 네스트 허브 부럽지 않은 HA전용 허브를 가질 수 있을 것이다.<br>
<img src="/assets/img/HA_HUB/HA_HUB_10.jpg" width="300"><br>

☆질문: 이럴거면 그냥 공기계를 무선충전거치대에 올려두면 되는거 아닌가?<br>
☆답변: 맞다. 그치만 조금 더 폼나지 않는가? 약간의 성취감은 덤이다.

