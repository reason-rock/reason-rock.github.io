---
title: Arguments (UpgradePrompt(old='22.2', new='22.2.2'),) 해결법
date: 2022-11-12 10:53:11 +9:00
categories: [Linux, (Ko)]
tags: [우분투, 리눅스, pip, pip버전, 파이썬]
---

pip 버전문제라는 것은 에러메세지를 보니 깨달았고, 쉽게 
```
pip3 install --upgrade pip
```

```
sudo python3 -m pip uninstall pip
sudo apt-get install python3-pip --reinstall
```
로 해결할 수 있을줄 알았는데, 어림도 없었고,

```
sudo pip3 install pip --upgrade
```


결국에는

```
sudo python3 -m pip uninstall pip
apt update
apt upgrade
reboot
```

완전히 다 지우고 나서
완전 재설치 해서

```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
```
두줄로 해결했다.
