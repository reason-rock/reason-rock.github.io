---
title: Jekyll-Chripy 테마 활용 깃허브 블로그 만들기
date: 2022-07-10 10:53:11 +9:00
categories: [Projects(Ko), GitHub Blog(Ko)]
tags: [깃허브, 블로그, 깃블로그, 깃허브 블로그, Jekyll, Chripy, Jekyll-Chirpy]
---

<h1>Jekyll-Chripy 테마 활용 깃허브 블로그 만들기</h1>
연초에 깃허브 계정을 만든 후 아직까지 깃허브에 올릴만한 수준의 코드를 짜지 못해 먼저 깃허브 블로그부터 만들어보자라고 생각했던 것이 벌써 6월이 되었다. <br>
미루고 미루다 틈틈히 도전해보았지만, 남들은 그렇게 쉽다던 블로그는 온갖 에러를 토해내며 날 놓아주지 않았다. <br>
이는 필시 본인이 벼락치기로 웹을 공부했기 때문일 것이다.(아니다) <br>
 <img src="/assets/img/GH_Blog/GH_History.png">
아직도 깃허브 휴지통을 살펴보면 수없이 많은 실패한 블로그 레포들이 나를 반겨준다. <br>

깃허브 블로그를 위해서는 ruby, jekyll,bundler 그리고 사용할 테마가 필요하다.
이번 설치에서는 Chirpy 테마를 사용한다.
https://github.com/cotes2020/jekyll-theme-chirpy


1. ruby 설치
```  
sudo apt install ruby
```
2. jekyll과 bundler 설치(*설치중에 permission error 발생시 sudo로 해결한다.)
```
gem install jekyll bundler
```
3. 사용할 테마 가져오기 (fork, starter 같은 더 쉬운 방법들도 있다고 한다. 이왕 하는 거 제대로 해 보겠다고 덤볐다가 6개월이 가버리는 일이 있으니 저 방법도 추천한다.)
```
git clone https://github.com/cotes2020/jekyll-theme-chirpy.git
```
여기까지 따라왔으면 절반은 성공한 것이다. <br>
이제 모든 환경을 구축한 것 같으니 신이나서
```
jekyll serve
```
를 입력하게 되면 뭔가 긴 에러가 발생하게 된다.
 <img src="/assets/img/GH_Blog/jekyll serve issue.png">


4. bundler 사용
```
bundler
```

5. jekyll serve를 통해 내부망에서 작동 확인
```
jekyll serve
```
정상적으로 진행되었으면 아래와 같은 화면을 볼 수 있을 것이다.
 <img src="/assets/img/GH_Blog/jekyllserve_complete.png">

터미널 상의 Server adress로 접속하면 데모 창을 확인할 수 있다.
 <img src="/assets/img/GH_Blog/initial_window.png">

여기까지 진행하였으면, 최소한의 테마 설치와 기본적 환경구축이 끝이 났다고 볼 수 있다.
이제 테마 커스터마이징, 깃허브 배포를 통해 이 대서사를 마무리 지을 수 있을 것이다.