---
title: GUI(lightdm)이 부팅때 자동으로 실행되지 않는 케이스
date: 2023-11-28 20:53:11 +9:00
categories: [Linux, Ubuntu]
tags: [ubuntu, GUI, lightdm, systemctl, service, dpkg]
---

lightdm이 부팅 때 자동으로 실행되지 않아 알 수 없는 CLI 기반으로 부팅되어,

`systemctl status lightdm.service`

명령어를 타이핑해서 서비스를 살려줘야만 작동되는 문제가 있었다.

그래서

`sudo dpkg-reconfigure lightdm`

패키지 재설치 등 여러 방법을 시도해 보았으나 먹히지 않았고

오랜 삽질 끝에 새로운 해결책을 찾을 수 있었다.

`rm /etc/systemd/system/default.target
systemctl set-default graphical.target`

왜인지는 모르겠으나 system default.target 경로가 잘못 지정되어 있었던 것으로 추정되며, 그에 따라 기존의 default.target를 삭제하고 새로 지정해 주니 정상적으로 작동이 되었다.

이렇게 해결이 된다는 사실을 확인한 후에서야 

`systemctl status lightdm.service`

`systemctl list-dependencies --reverse lightdm.service`

를 했을 때 graphical target에 녹색 불이 들어오지 않았었다는 것을 깨달았다.

아마 그것이 링크가 되지 않아서였던 것이 아닐까..
