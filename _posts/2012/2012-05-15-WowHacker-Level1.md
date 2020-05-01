---
title: "[와우해커/wowhacker] Level 1 문제풀이"
date: 2012-05-15 
layout: post
category: WarGame
tags:
  - Security
  - Web
  - Hacking
  - 와우해커
comments: true
---

**[
http://webgame.wowhacker.com/](http://webgame.wowhacker.com/)**



1학년때 조금 풀다가 말아버린 웹게임사이트이다!

다시한번 열심히 풀어보자구^^!



<!-- more -->

----



> 이 포스팅은 기존 개발 블로그에서 백업한 포스팅입니다.
>
> * 원문 : https://syung1104.blog.me/157696019



----



### Level 1 문제

![](https://github.com/yenarue/images/blob/master/wowhacker/level1/WHlevel1.jpeg?raw=true)



우옹 드디어 첫 문제다!

php코드를 봐야한단다. 첫 문제니 쉽겠지?.?

일단, 문제에 있는 링크 http://webgame.wowhacker.com/level1.php 로 들어가 보자







![img](https://github.com/yenarue/images/blob/master/wowhacker/level1/WHlevel1-00.jpeg?raw=true)



느닷없이 키 파일을 열수 없다는 말이 나온다.

여기서 마우스 오른쪽 클릭 - 페이지소스를 보게되면.... 당연히 php코드가 나오지 않는다^^;







### 여기서의문ㅋ

HTML소스는 아주 잘 보이는데 왜 PHP코드는 페이지소스보기로 보이지 않는 것일까?



HTML는 서버에서 소스를 가져와 클라이언트단에서 처리하는 방식이기 때문에,

페이지소스보기로 볼 수 있는 것이다.

하지만 PHP는 서버가 처리하여 결과물만을 클라이언트에게 보내주는 방식이기 때문에

페이지소스보기에도 결과물만 나오는 것이다!







### 힌트

하지만 힌트에 php파일의 소스코드를 웹에서 보기위한 방법을 찾아보라고 나와있다

친절하당 훈훈해

☺️



### 솔루션

**웹에서 php파일 소스코드를 보는 방법은 php문서 확장자에 s를 첨가하는 것이다.**

(phps : PHP Source의 약자로서 해당 php문서의 소스를 불러오게 된다)





﻿![img](https://github.com/yenarue/images/blob/master/wowhacker/level1/WHlevel1-01.jpeg?raw=true)

위와 같이 확장자명을 .phps로 바꿔주면 웹에서도 php소스코드를 볼 수있다.

이렇게 php소스코드가 공개된다면 정보가 유출될 가능성이 높으니, 당연히 대부분의 웹페이지에서는 이러한 일이 생기지 않게 설정해놓는다고 한다.







소스코드를 살펴보면, Get메소드로 key값을 가져오며 key값이 `wowhacker_hardware`이면, 정답을 출력하는 것을 알 수 있다.







Get메소드식으로 값을 가져오는 것이므로 URL을 이용하여 파라미터값을 넘기게 될 것이다.

`http://webgame.wowhacker.com/level1.phps?key=wowhacker_hardware` 를 주소창에 써보자





![img](https://github.com/yenarue/images/blob/master/wowhacker/level1/WHlevel1-02.jpeg?raw=true)





위와 같이 정답이 나타나게 된다.



### 마무리

역시 레벨1은 쉽다쉽다ㅋ

으으 몇문제나 풀 수 있을까@0@