---
title: 크롬 'no longer matches that of your login keyring' 에러 해결
date: 2023-11-26 20:53:11 +9:00
categories: [Linux, Ubuntu]
tags: [ubuntu, chrome, whale, keyring, gnome]
---

'the password you use to login to your computer no longer matches that of your login keyring'
해당 에러는 네이버 웨일을 우분투에 설치하던 중 발견했다. 크롬 기반 브라우저, 키링을 사용하는 다른 프로그램 모두 다 해당할 것으로 생각된다.

본인의 경우 우분투에서 여러 계정을 사용중인데, 모든 비밀번호를 입력해도 로그인이 안돼서 알아보니 키링 비밀번호가 다르거나, 오래된 정보가 남아있을 경우라고 한다.

우분투 21 이상 버전의 경우
```
killall -9 gnome-keyring-d
cd ~/.local/share/
rm -rf keyrings
```
,

우분투 21 이하 버전의 경우
```
killall -9 gnome-keyring-daemon
rm -fr ~/.gnome2/keyrings/
```

로 키링 데이터를 전부 삭제한 후 다시 실행하여 해결할 수 있다.