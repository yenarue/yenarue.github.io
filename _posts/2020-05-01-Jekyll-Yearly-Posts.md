---
title: "[Jekyll] GitHub 블로그 포스팅들을 연도별로 분류하기"
date: 2020-05-01 22:30  
layout: post
category: Tip
tags:
  - Jekyll
  - 블로그
comments: true
---

네이버 블로그의 포스팅들을 깃허브 블로그로 옮기는 중이다. 처음 글을 올렸던 2012년의 포스팅부터 옮기다보니 깃허브 블로그가 왠지 어수선해보이는 것 같다 😂...

깔끔한 관리를 위해, 포스팅을 연간으로 모아보는 메뉴를 만들고 싶어졌다.

<!-- more -->

## 메뉴 추가는 어떻게?

Jekyll 블로그의 경우, `blog` 디렉토리에 메뉴의 내용(content)을 정의할 수 있게 되어있다.

메뉴를 추가하고 싶으면, `blog` 디렉토리에 파일을 하나 생성하고 `_config.yml` 파일에 메뉴로서 지정해주면 된다!

## 포스팅들을 연도별로 모아보는 메뉴를 만들자!

### 메뉴 만들기

나는 년도별로 포스팅을 그룹핑하여 보고싶다!

일단 `blog` 디렉토리에 메뉴 파일을 하나 만들어보자!

이름은 "모아본다" 는 뜻으로 `archive.html` 라고 지었는데... 음... 별로인 거 같기도..

코드는 다음과 같다 : 

<script src="http://gist-it.appspot.com/https://github.com/yenarue/yenarue.github.io/blob/master/blog/archive.html"></script>

사이트의 모든 포스팅을 가져온 뒤, 년도로 모아 보여주는 코드다. `site.posts` 는 어차피 포스팅들이 날짜 순으로 들어있기 때문에 그냥 다음 포스팅과 비교하는 코드로 작성했다.

> 하는 김에 포스팅 날짜도 한국식으로 보여지게 변경했다. 은근 보기 불편했는데 시-원!

### 메뉴 추가하기

이제 방금 작성한 메뉴를 블로그에 추가해보자!

Jekyll은 빌드 후에 `blog` 디렉토리에 있던 메뉴들을 각각 디렉토리로 만들어낸다. 즉, 아까 만든 `/blog/archive.html` 를 해석해서 `/blog/archive/` 로 만들어낸다는 뜻이다. 

`_config.yml` 파일에 `/blog/archive/`  를 아래와 같이 추가했다 :

<script src="http://gist-it.appspot.com/https://github.com/yenarue/yenarue.github.io/blob/master/_config.yml?slice=38:48"></script>

메뉴 이름은 직관적으로 "Yearly" 라고 지었다!

그럼 레포지토리에 push 하고 결과를 살펴보자! 



## 마무리

### 완성된 메뉴
![](https://github.com/yenarue/images/blob/master/jekyll/yearly-archive-menu.png?raw=true)
### 완성된 페이지
![](https://github.com/yenarue/images/blob/master/jekyll/yearly-archive.png?raw=true)

연도별로 나뉘니 정말 깔끔하고 좋다!

뭔가 괜히 각 연도별로 포스팅 비교가 한눈에 되니까 더욱 더 새로운 포스팅을 열심히 하고싶은 마음 + 기존 블로그의 글들을 빨리 백업하고 싶은 마음이 뿜뿜거리는 것 같다!ㅋ_ㅋ

깔끔하게 확인도 할 수 있고 포스팅 동기부여도 되고 일석이조! ☺️



이제 더 열심히 네이버 블로그의 포스팅들을 옮겨오도록 하자!!!!!! 하핫!!!!ㅋ



## 참고자료

* [[StackOverflow] Jekyll/Liquid Templating: How to group blog posts by year?](https://stackoverflow.com/questions/19086284/jekyll-liquid-templating-how-to-group-blog-posts-by-year)

