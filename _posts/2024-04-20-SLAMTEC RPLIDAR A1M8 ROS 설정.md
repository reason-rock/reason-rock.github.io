---
title: SLAMTEC RPLIDAR A1M8 ROS 설정
date: 2024-04-20 20:53:11 +9:00
categories: [Device Overview, LIDAR]
tags: [LIDAR, rplidar, ROS, SLAMTEC]
---

2D 라이다 중 가장 흔히 사용되는 RPLIDAR를 사용해보게 되었다.
아두이노, 라즈베리파이, 젯슨, 일반 PC등 다양한 환경에서 사용되는 제품 답게 ROS 드라이버 또한 지원되었다.

![RPLIDAR_0](https://github.com/reason-rock/reason-rock.github.io/assets/98293904/f35ed5c9-099e-4ea0-9422-c2061b341ca9)


워크스페이스 폴더/src로 이동 후 드라이버를 다운받아보자

`git clone https://github.com/Slamtec/rplidar_ros.git`

`catkin make`를 통해 빌드하고

`roslaunch rplidar_ros view_rplidar_a1.launch`

를 통해 실행하면

rviz에서 scan 데이터를 확인할 수 있다.


![RPLIDAR_1](https://github.com/reason-rock/reason-rock.github.io/assets/98293904/453d7085-f499-488b-80d9-d9d670bb5731)

![RPLIDAR_2](https://github.com/reason-rock/reason-rock.github.io/assets/98293904/4d369b73-c851-4566-9d05-36550d70c396)