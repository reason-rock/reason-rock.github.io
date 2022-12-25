---
title: AttributeError module 'serial' has no attribute 'Serial' 해결
date: 2022-12-17 10:53:11 +9:00
categories: [Linux, (Ko)]
tags: [AttributeError, serial, 시리얼, nmea, pyserial, PermissionError]
---

GPS 설정 중에 혹시나 시리얼 모듈이 문제인가 싶어서 재설치 하고 뭐하고 이것저것 하다가 포기하고 잤던 다음날, 다른 MRP 에서는 잘 돌아갔던 nmea 패키지조차 켜지지 않았다.

```
"Traceback (most recent call last):
  File "/opt/ros/noetic/lib/nmea_navsat_driver/nmea_topic_serial_reader", line 38, in <module>
    libnmea_navsat_driver.nodes.nmea_topic_serial_reader.main()
  File "/opt/ros/noetic/lib/python3/dist-packages/libnmea_navsat_driver/nodes/nmea_topic_serial_reader.py", line 70, in main
    GPS = serial.Serial(port=serial_port, baudrate=serial_baud, timeout=2)
 AttributeError: module 'serial' has no attribute 'Serial'"
```

어찌어찌 하다가 엎어져 잤기에, 뭘 했는지에 대한 기억이 없었다.

그래서 오늘도 시작하는 삽질기

nmea 문제인가 싶어서 재설치 해보았으나 어림도 없었고, 모듈이 없다길래 pip install serial, pip install pyserial 다 해봤지만 이미 존재한다는 답만 돌아왔다.

그래서 싸그리 다 밀고 다시 깔아보자는 생각으로
pip uninstall serial을 통해 serial을 제거하고 pyserial을 재설치 하려고 했는데 늘 그렇듯 새빨간 에러가 나의 앞길을 막았다.

"PermissionError: [Errno 13] Permission denied: 'WHEEL'" 

듣도 보도 못하던 문제였는데, 뭐 Permission 에러기에 sudo 하면 되겠거니 싶었다.
```
sudo pip uninstall serial
pip install --upgrade --force-reinstall pyserial
```
그래서 했다.

그리고 블로그 글을 쓰던 중 pip에 sudo를 붙여도 된다고 당당하게 글을 써도 되나 싶어서 찾아보니 하지 않는게 좋단다.

pip에 sudo를 붙이는건 보안측면에서 위험하다고. 생각해보면 하지말라는 걸 해서 좋을건 없지 않겠는가.

그래서 대안으로
```
pip3 install 패키지 --user
```
를 제시하니 가능하면 이것을 사용하는게 안전할 것이다.


해결!

1. AttributeError: module 'serial' has no attribute 'Serial'"는 그냥 serial 모듈이 아닌 pyserial module를 깔아야 한다.
2. pip에도 sudo를 붙일 수 "는" 있다.
3. 그럼에도 불구하고 위험하니 가능하면 pip3 install 패키지 --user을 사용하는 것이 안전하다.