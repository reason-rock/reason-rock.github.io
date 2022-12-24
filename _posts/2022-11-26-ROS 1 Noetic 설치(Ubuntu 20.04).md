---
title: ROS 1 Noetic 설치(Ubuntu 20.04)
date: 2022-11-26 10:53:11 +9:00
categories: [Ros, Ros_Ko]
tags: [우분투, 리눅스, ROS1, noetic, ROS설치]
---

텐서플로우 gpu 설정을 위한 삽질 과정에서 우발적으로 우분투 싹 밀고 22.04로 올렸다가 보기좋게 실패한 후 다시 20.04로 내려왔다.
물론 백업따위 해두지 않았기에, ros를 다시 설치해야 했다.

이럴 때 마다 매번 ROS 위키를 찾아 들어가기 귀찮아서 이참에 아예 여기 저장하기로 했다.

1. repository 추가
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```


2. 설치
```
sudo apt update
sudo apt install ros-noetic-desktop-full
```

3. bash 설정
```
source /opt/ros/noetic/setup.bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

4. 추가설치
```
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
sudo rosdep init
rosdep update
```

+유튜브 강의나 책을 보니 이렇게도 설치가 가능하다고 한다(한줄설치)
```
wget -c https://raw.githubusercontent.com/qboticslabs/ros_install_noetic/master/ros_install_noetic.sh && chmod +x ./ros_install_noetic.sh && ./ros_install_noetic.sh
```