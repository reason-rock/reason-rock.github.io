---
title: 도전! SLAM 시리즈-외전 - SLAM pcd map 파일 간단히 보기
date: 2023-02-20 10:53:11 +9:00
categories: [Projects(Ko), SLAM]
tags: [SLAM, LIDAR, velodyne, PCD, PCL, python3-pcl, ]
---

SLAM을 통해 PCD 맵을 뽑아냈다.
그럼 이걸 볼려면 어떻게 해야 할까?
많은 방법이 있지만 최대한 간단한 방법을 가지고 와봤다.

바로 pcl-tools에 내장된 pcl_viewer

먼저 python3-pcl을 설치해주자
`sudo apt install python3-pcl`

그 후 pcl-tools를 설치하자
`sudo apt install pcl-tools`

터미널을 연 후
`pcl_viewer GlobalMap.pcd`
를 입력하면?

<img src="/assets/img/PCD_viewer/PCD_viewer.png" alt="PCD 파일을 pcl_viewer로 연 화면"><br>

맵을 바로 볼 수 있다.
