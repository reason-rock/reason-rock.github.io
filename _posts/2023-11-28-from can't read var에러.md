---
title: "파이썬 from: can't read /var/mail/ 에러"
date: 2023-11-28 22:53:11 +9:00
categories: [Linux]
tags: [python, pygame, var, Shebang, env]
---

파이썬으로 ROS 퍼블리셔 짜는 중에

from: can't read /var/mail/pygame

에러가 발생했다.

설마 ros에 joy 패키지가 있으니 pygame은 호환이 안되는게 아닌가? 라는 불길한 생각이 들며 슬퍼졌다.

하지만 해답은 다행히, 그리고 허무하게도

에러 메세지를 보니 인터프리터를 잘못 잡은 것 같아

코드 제일 위에 Shebang으로

`#!/usr/bin/env python` 

인터프리터를 지정해 주니 정상적으로 동작했다.
