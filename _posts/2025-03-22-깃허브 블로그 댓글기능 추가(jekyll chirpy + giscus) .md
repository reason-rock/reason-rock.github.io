---
title: 깃허브 블로그 댓글기능 추가(jekyll chirpy + giscus) 
date:  2025-03-22 20:53:11 +9:00
categories: [Projects, GitHub Blog]
tags: [깃허브 블로그, Jekyll, Chirpy, giscus, 댓글 기능, GitHub Pages, 블로그 설정]
---

처음에는 Disquas가 가장 위에 노출되길래 이걸 하려고 했는데 가입하는 도중에 이 페이지를 보고 바로 탈퇴하게 된다.
![Image](https://github.com/user-attachments/assets/15295af2-ed5a-4984-86f0-348c3f852bbf)

그래서 giscus를 가지고 해보기로 했고,

의외로 가이드가 잘 되어 있었다.

<https://giscus.app/ko>

한국어 가이드가 있고
레포 이름을 입력해주면 된다.
그 전에

<https://github.com/apps/giscus>

에서 앱을 설치해주어야 한다고 한다. 깃허브에서 앱은 생소한 개념인데...

![Image](https://github.com/user-attachments/assets/320590d1-96d7-4276-8c01-b0e8fc46737f)

적용할 레포 하나에만 접근하도록 해주었다.

Discussion도 해줘야한다. 세팅에 바로 있다

![Image](https://github.com/user-attachments/assets/294b171b-eeca-4827-9b40-c4dc56952eb0)


![Image](https://github.com/user-attachments/assets/aceb5dfb-0263-4733-a64b-d491ec34ab49)

그 뒤로는 쉽다.

만들어진 스크립트를
_config.yml에 각 항목에 맞게 붙여넣는다.
optional은 하나도 안건드려도 괜찮다.

하지만 함정이 한가지 있다.

기본 템플릿에는

```provider: giscus```
이 되어있는데 이를

```active: giscus```
로 바꿔줘야 한다.