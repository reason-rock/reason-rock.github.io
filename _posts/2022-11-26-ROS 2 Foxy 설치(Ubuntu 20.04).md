---
title: ROS 2 Foxy 설치(Ubuntu 20.04)
date: 2022-11-26 10:53:11 +9:00
categories: [Linux, ROS2]
tags: [우분투, 리눅스, ROS2, Foxy, ROS설치]
---




# ROS2-Foxy 설치
텐서플로우 gpu 설정을 위한 삽질 과정에서 우발적으로 우분투 싹 밀고 22.04로 올렸다가 보기좋게 실패한 후 다시 20.04로 내려왔다.
물론 백업따위 해두지 않았기에, ros2를 다시 설치해야 했다.

이럴 때 마다 매번 ROS 위키를 찾아 들어가기 귀찮아서 이참에 아예 여기 저장하기로 했다.


1. 로케일 세팅
```
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
```

2. repository 추가
```
sudo apt update
sudo apt install curl gnupg2 lsb-release
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo sh -c 'echo "deb [arch=$(dpkg --print-architecture)] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
```

3. 진짜 설치
```
sudo apt update
sudo apt install ros-foxy-desktop
```

4. bash파일 설정
```
source /opt/ros/foxy/setup.bash
```

5. 설치 확인 - 개인적으로 ros2에서 제일 마음에 드는 부분
```
ros2 run demo_nodes_cpp talker
ros2 run demo_nodes_py listener
```

6. 부가 설치
```
sudo apt install -y python3-pip
pip3 install -U argcomplete
sudo apt install python3-colcon-common-extensions
```


끝!