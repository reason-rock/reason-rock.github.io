---
title: C++ internal compiler error 해결
date: 2022-12-17 13:53:11 +9:00
categories: [Linux, (Ko)]
tags: [우분투, 리눅스, C++, 컴파일러, compiler, 스왑 메모리, swap, swapoff, swapfile]
---




열심히 PCL을 빌드하며, 온갖 에러들을 헤치고 이젠 무조건 된다! 라는 생각을 하는 순간
c++: internal compiler error를 맞닥들였다.

다행히(?) 이 에러는 코드나 패키지의 에러가 아니었는데, 메모리 쪽 문제라 스왑 메모리를 재설정 하면 된다고 한다.
먼저 swap 메모리에 있는걸 싸그리 날린 후,
```
sudo swapoff -a
```

메모리를 리사이즈 해준다.
```
sudo dd if=/dev/zero of=/swapfile bs=1G count=8
```

그후 Swap 파일을 만들고, 활성화 해준다


```
sudo mkswap /swapfile
#만들고
sudo swapon /swapfile
#활성화
```



아래 명령어를 통해 Swap에 대한 정보를 확인할 수 있다.
```
grep SwapTotal /proc/meminfo
```
