---
title: NUMA node read from SysFS had negative value -1 에러
date: 2023-03-16 22:53:11 +9:00
categories: [Linux, Ubuntu]
tags: [우분투, 리눅스, 마운트, 외장하드, usb, ntfsfix]
---

해당 에러는 GAN이 한창 쏟아져 나올때 와! 그림! 와! 채색!이라는 생각에 그림 똥손이던 나도 기계의 힘을 빌리면 금손이 될 수 있을까 라는 행복회로로 포켓몬 채색 GAN을 돌려보기 위해 삽질했던 과정이다.

CUDA 와 Cudnn을 모두 설치하고 학습을 돌리다 보면 중간에 이런 에러가 뜨면서 뻗는데, 

Cannot set memory growth on device when virtual devices configured
failed to create cublas handle: cublas_status_not_initialized
cannot set memory growth on device when virtual devices configured
op_requires failed at conv_ops.cc:1106 : not found: no algorithm worked!

NUMA node read from SysFS had negative value -1

어렵사리 설치하고 이제 끝이라고 좋아하고 있다가 다시 절망에 빠져들었다.

일단 에러 로그 마지막 줄부터 확인해보자

NUMA가 있긴 한데, 음수이다? 뭐지 그래픽카드가 안잡힌건가

```
lspci | grep -i nvidia
```

를 입력하면 01:00.0 VGA ~~~~~ 를 볼 수 있다.

분명 그래픽카드가 잡히긴 잡혔다는 의미이다.

```
cd sys/bus/pci/devicecs/
ls

```

를 통해 해당 경로에 위치한 장치들을 보면 0000:이 추가된 그래픽카드가 있다.

```
cat /sys/bus/pci/devices/0000\\:01\\:00.0/numa_node

```

에러 메세지와 같이 -1을 가져온다.

이제 이것을 0으로 바꾸어주면 문제가 해결될 것 같다

```
echo 0 | sudo tee -a /sys/bus/pci/devices/0000\\:01\\:00.0/numa_node

```

아까 -1이 나왔던 값을 다시 확인해본다.

```
cat /sys/bus/pci/devices/0000\\:01\\:00.0/numa_node

```

이제 정상적으로 0이 나온다.

한가지는 해결