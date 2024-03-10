---
title: No velodyne_pointcloud/point_types.h 에러 해결
date: 2023-01-13 20:53:11 +9:00
categories: [Projects, SLAM]
tags: [SLAM, LIDAR, velodyne, point_types.h,PCL, ROS, noetic]
---

남이 짜놓은 패키지를 돌리는거는 어느정도 감을 잡은 것 같아 이제 PCL을 처음부터 차근차근 배워가고자 PCL 위키를 보고 따라하기 시작했다.

첫날부터 분명 ROS PCL 위키에 있는 예제 코드와 이곳저곳에서 줏어온 코드를 돌렸을 뿐인데 에러가 떴다.
심지어 지금은 없지만 예전에 rviz로 시현까지 해 보았던 velodyne이었기에 패키지 문제는 아닐것이라 생각했는데 알고보니 해결책은 간단했다.
velodyne_pointcloud는 특정 ROS 버전 이후로 velodyne_pcl로 바뀌었다는 것 같았고, 단순히 velodyne_pointcloud를 velodyne_pcl로 바꾸면 정상적으로 작동하였다.
