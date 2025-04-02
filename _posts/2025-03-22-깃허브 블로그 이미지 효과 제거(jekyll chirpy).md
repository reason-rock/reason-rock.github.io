---
title: 깃허브 블로그 이미지 효과 제거(jekyll chirpy)
date:  2025-03-22 20:53:11 +9:00
categories: [Projects, GitHub Blog]
tags: [깃허브, 블로그, 깃블로그, 깃허브 블로그, Jekyll, Chripy, Jekyll-Chirpy, 무한로딩, 이미지, shimmer, shimmer effect]
---

어느 순간부터 이미지에 불빛이 번쩍거리는 효과가 들어가기 시작했다.
처음에는 로딩인가 했는데 로딩이 완료되어도 계속 유지되는 문제가 있었다.
그런데 이 효과의 이름이 뭔지를 모르니 검색도 못하고 끙끙대고 있었다.
다행히 F12가지고 확인하니 shimmer effect라고 했다.
그걸 가지고 검색하니 chirpy 테마의 버그라고 한다.
원래는 로딩할때만 잠깐 나타나야 한다는듯?

해결책은 간단하다.

assets/css/jekyll-theme-chirpy.scss에
```
.shimmer::before{
  background:none;
}
```
을 추가하면 없어진다.

끝.