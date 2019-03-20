---
layout: post
title: Mac/Linux - alias 설정
tags:
- MAC
- Linux
- alias


---

mac의 `\user\사용자\` 위치에서 `vi ~/.cshrc.user alias` 입력해서 alias를 등록해준다.

양식은  `alias 단축어='명령어'` 로 입력해주면 된다. 이걸 저장해준 후 `source ~/.cshrc.user` 명령어를 쳐서 파일로딩을 해주면 alias 등록이 된다.

alias파일내에서 #뒤의 내용은 주석처리 됨.