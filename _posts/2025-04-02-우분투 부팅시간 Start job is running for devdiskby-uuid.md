---
title: 우분투 부팅시간 Start job is running for /dev/disk/by-uuid/
date:  2025-04-02 12:53:11 +9:00
categories: [Linux, Ubuntu]
tags: [우분투, 듀얼부팅, 멀티부팅, 윈도우, 리눅스, 부팅, UUID, Start job, ubuntu, fstab, initramfs]
---

듀얼부팅 상태에서 윈도우를 재설치하고, 우분투가 잡히지 않는 문제를 해결하였으나 하나의 문제가 더 있었다.
우분투 선택시 부팅 시간이 너무나 길다는 것이었다. 부팅과정을 지켜보니 Start job is running for /dev/disk/by-uuid/ 에서 1분30초를 대기하느라 그렇게 된 것이었다.
파티션을 잡지 못하는 것 같았는데, 아무래도 윈도우 재설치시 UFI 파티션을 같이 지워버렸던 것 같다.


그래서

```sudo nano /etc/fstab```

에서 해당 파티션을 찾는 줄을 주석처리하고

```sudo update-initramfs -u```

initram을 업데이트 시키니
부팅이 20초 이내로 정상화되었다.
