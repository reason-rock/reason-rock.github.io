---
title: YDLIDAR 4ROS ROS 설정
date: 2024-04-20 20:53:11 +9:00
categories: [Device Overview, LIDAR]
tags: [LIDAR, 4ROS, ROS, YDLIDAR]
---

지난번에 RPLIDAR를 사용해 본 것에 이어 YDLIDAR 사의 4ROS를 사용해 보게 되었다.
YDLIDAR 사는 나름 이름 있는 브랜드인 것으로 알고 있는데, 이 제품은 생소했다.
창고에 있던 키트에 달려있던 제품이라 어쩔 수 없이 쓰게 되었는데 rplidar보다는 ros 실행이 조금 더 복잡했다.
드라이버 외에도 SDK를 설치해야 했기 때문이다.


1. 드라이버 설치

워크스페이스 폴더/src로 이동 후 드라이버를 다운받아보자

`git clone https://github.com/YDLIDAR/ydlidar_ros_driver.git`

`catkin make`를 통해 빌드하고

`roslaunch ydlidar_ros_driver 4ros_lidar_view.launch`

를 통해 실행하면

rviz에서 scan 데이터를 확인할 수 있다.

2. SDK 설치

2.1 필요 패키지 설치
```
sudo apt install cmake pkg-config
sudo apt-get install python swig
sudo apt-get install python-pip
```

2.2 SDK 설치
```
git clone https://github.com/YDLIDAR/YDLidar-SDK.git
cd YDLidar-SDK/build
cmake ..
make
sudo make install
```

2.3 설치확인

`./tri_test`


![4ROS_1](https://github.com/reason-rock/reason-rock.github.io/assets/98293904/3feff044-f621-4604-9273-10227673602a)

![4ROS_2](https://github.com/reason-rock/reason-rock.github.io/assets/98293904/cb87e02d-a70b-4c57-94ea-7fc578f3b415)


<iframe width="560" height="315" src="https://www.youtube.com/embed/GztbBGHplKE?si=xl3CDOwVMGdcSsFY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>