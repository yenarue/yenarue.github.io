---
title: "Github 블로그 검색엔진에 등록하기 (구글/네이버/다음)"
date: 2020-04-30 
layout: post
category: Tip
tags:
  - SEO
  - 검색엔진
  - 블로그
comments: true
---

GitHub 블로그를 본격적으로 사용하기 위해 검색엔진에 등록을 하기로 했다. 

일단은 **구글, 네이버, 다음**에 등록을 해보려 한다. 각 포털사이트별로 검색엔진에 등록할 수 있는 기능들을 제공하는데, 해당 기능들도 계속해서 업데이트 되는 듯 하다. ~~그들도 놀고 먹지는 않을테니 당연한 것이겠지만...~~  검색엔진 등록방법을 구글링을 해보니 대부분 예전 버전을 기준으로 작성되어 있어서 현재와는 메뉴 구성이나 사용법이 좀 다른 것 같아, 최신버전으로 포스팅을 작성해봤다.

<!-- more -->

----

**👀목차**

* TOC
{:toc}


---




# 1. 검색엔진에 등록할 준비하기

## sitemap.xml 생성하기

우선 검색엔진에서 GitHub 블로그의 글들을 긁어올 수 있도록, 사이트의 모든 페이지 정보를 모아두는 `sitemap.xml` 이 필요하다.

`sitemap.xml` : 

![](https://github.com/yenarue/images/blob/master/2020-seo/sitemap.png?raw=true)

위와 같이 페이지 정보들이 모두 들어가 있어야 하는데, 포스팅을 업로드 할 때마다 매번 추가해주는 건 여간 번거로운 일이 아닐 수 없다.

👩🏻‍💻 우리는 개발자이므로 이를 자동화해주는 간단한 스크립트를 짜서 넣어보도록 하자! 

아래의 코드를 복붙하여  `sitemap.xml` 파일을 만들고 루트 디렉토리에 추가하자.
https://github.com/yenarue/yenarue.github.io/blob/master/sitemap.xml

업로드 후, `https://블로그주소/sitemap.xml` 에 접속해서 내 블로그의 모든 페이지 주소를 정상적으로 출력하는지 확인해보자!



### 포스팅 작성시 sitemap 설정하기

포스팅 작성 시, 포스팅 정보를 입력하는 head 부분에 사이트맵 관련 설정을 추가할 수 있다.

```mardown
---
... title, date 등 생략
lastmode: 2020-04-28 13:00:00
sitemap:
  changefreq: daily
  priority : 1.0
---
```

* lastmode : 마지막 수정일
* sitemap.changefreq : 스크랩 주기 (데일리, 위클리 등...)
  * 너무 짧게 설정하면 스크랩이 잦아져 트래픽에 안좋은 영향을 미칠 수 있다!
* sitemap.priority : 스크랩 우선순위

그럼 포스팅 작성시마다 매번 위 설정을 넣어줘야 하는걸까?ㅠㅠ 귀찮다... 귀찮아...

나는 귀찮은게 싫어서 개발자가 된 것이기 때문에 `sitemap.xml` 에 디폴트 설정을 아래와 같이 넣어두었다.

* lastmode : date와 같은 값
* sitemap.changefreq : weekly
* sitemap.priority : 0.5



## robots.txt 생성하기

사이트를 검색엔진에 등록하면 검색엔진의 크롤러가 사이트에 방문하여 크롤링을 해간다.

이 때, 크롤러가 방문했을 때 참고할 수 있는 정책을 명시해주면 좋다.

아래의 코드를 복붙하여 `robots.xml` 파일을 만들고 루트디렉토리에 추가하자.

https://github.com/yenarue/yenarue.github.io/blob/master/robots.txt



## feed.xml 생성하기

준비하는 김에 RSS Feed로도 등록될 수 있게 `feed.xml` 까지 만들어보자!

아래의 코드를 복붙하여 `feed.xml` 파일을 만들고 루트디렉토리에 추가하자.

https://github.com/yenarue/yenarue.github.io/blob/master/feed.xml

<br/>


자 그럼 이제 검색엔진에 등록할 준비는 모두 끝! 🙌🏻

<br/>


# 2. 검색엔진에 등록하기

블로그는 검색엔진에 등록될 준비를 마쳤으므로 이제 진짜 등록을 해보자!

## 구글 (Google)

구글은 검색엔진 등록 방법을 계속해서 개선하고 있는 것 같다.

1. [구글 웹마스터 도구](https://search.google.com/search-console?hl=ko&utm_source=wmx&utm_medium=deprecation-pane&utm_content=home&resource_id=https://yenarue.github.io/) 접속 ->  `URL 접두어` 탭으로 이동 -> 등록하고자하는 사이트의 URL 입력 -> `계속` 버튼 클릭

   ![](https://github.com/yenarue/images/blob/master/2020-seo/google-1.png?raw=true)

2. 그럼 자동으로 Google Search Console 로 이동된다.

3. 좌측 메뉴에서 `Sitemaps` 을 클릭 -> `새 사이트맵 추가` 에 `https://깃헙주소/sitemap.xml` 을 입력 -> `제출` 버튼 클릭

   ![](https://github.com/yenarue/images/blob/master/2020-seo/google-2.png?raw=true)

4. 아래와 같이 나타나면 성공이다.

   ![](https://github.com/yenarue/images/blob/master/2020-seo/google-3.png?raw=true)

다른 메뉴들을 클릭해보니 데이터 수집중이라는 표시가 뜬다. 아무래도 검색엔진이 일을 다 하려면 시간이 걸리는 듯 하다. 몇일 뒤 다시 체크해보는 것으로.......
![](https://github.com/yenarue/images/blob/master/2020-seo/google-wait.png?raw=true)


## 네이버 (Naver)

국내 대표 포털 사이트인 네이버에도 등록을 해보도록 하자.

1. [네이버 서치어드바이저](https://searchadvisor.naver.com/) 에 접속한다

2. `웹 마스터 도구` -> `사이트 관리` -> `사이트 등록` 페이지로 이동한다

   ![](https://github.com/yenarue/images/blob/master/2020-seo/naver.png?raw=true)

3. URL을 입력하고 엔터를 친다

4. `사이트 소유확인` 페이지에서 `HTML 파일 업로드` 를 선택한다

5. `HTML 확인 파일` 을 클릭하여 다운로드한다

6. 등록하고자하는 사이트의 루트 디렉토리에 해당 파일을 업로드한다.

7. 가이드 되어있는 링크를 클릭하여 제대로 업로드 되었는지 확인한다.

8. `소유확인` 버튼을 누른 후 아래와 같은 팝업이 뜨는지 확인한다.

   ![](https://github.com/yenarue/images/blob/master/2020-seo/naver-notice.png?raw=true)

    나의 경우에는 이 단계에서 하루종일 오류가 떴었다. 

     >HTML 확인파일을 찾을수 없거나, 네이버 검색로봇 사이트 서버에 접근할 수 없습니다.

     대충 이런 문구가 떴었는데 (스샷 없음ㅠㅠ), 다음날 다시 시도해보니까 정상적으로 진행되었다.

     혹시 이런 문구가 계속 뜬다면 맘편히 하루정도 더 기다려보도록 하자 😅

9. 목록으로 돌아와서 아래와 같이 정상등록되었음을 확인하자.

   ![](https://github.com/yenarue/images/blob/master/2020-seo/naver-completed.png?raw=true)


### 사이트맵 제출하기

![](https://github.com/yenarue/images/blob/master/2020-seo/naver-completed.png?raw=true)

1. 등록된 블로그 링크를 클릭하여 [사이트 관리] 페이지로 진입한다.

2. `요청` -> `사이트맵 제출` 메뉴로 진입한다.

3. 아까 만들어서 업로드했던 `sitemap.xml` 의 주소를 다음과 같이 입력하고 [확인] 버튼을 누른다.

   ![](https://github.com/yenarue/images/blob/master/2020-seo/seo-naver-sitemap.png?raw=true)

4. 잘 등록되었는지 확인한다.

   ![](https://github.com/yenarue/images/blob/master/2020-seo/seo-naver-sitemap-2.png?raw=true)

### 그 외

* 네이버 웹마스터 도구의 [사이트 간단 체크] 메뉴를 잘 활용하면 내 사이트에 어떤 설정이 부족한지 체크할 수 있어 매우 유용하다.

  ![](https://github.com/yenarue/images/blob/master/2020-seo/naver-seo-check.png?raw=true)

* 아래 화면에서 등록된 사이트의 링크를 클릭하면 리포팅을 확인할 수 있다.

  ![](https://github.com/yenarue/images/blob/master/2020-seo/naver-completed.png?raw=true)

  ![](https://github.com/yenarue/images/blob/master/2020-seo/naver-report.png?raw=true)

  특이한 점은 이 메뉴는 네이버 웨일로만 접속이 된다는 점이다. (나만 그런가...) 크롬으로 접속하면 아래와 같은 화면이 나타난다.

  ![](https://github.com/yenarue/images/blob/master/2020-seo/naver-report-error.png?raw=true)
  
  [2020.05.03 내용 추가] 오늘 크롬으로 접속해보니 정상적으로 접속된다. 뭐지?ㅎㅎ


## 다음 (Daum)

국내 2위 포털 사이트인 다음에도 등록해보자! 일단 다음이 제일 심플했다.

1. [다음 검색등록](https://register.search.daum.net/index.daum) 에 접속한다.
2. `블로그 등록` 을 클릭하고 블로그 URL을 넣고 `확인` 을 클릭하면 끝이다!

![](https://github.com/yenarue/images/blob/master/2020-seo/daum.png?raw=true)



# 3. 검색엔진 최적화하기 (진행중)

포스팅이 잘 검색 될 수 있도록 metadata 태그를 추가하면 좋을 것 같아서 찾아보는 중이다. 

* [[Jekyll Plugin] jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag)
* [블로그에 SEO 적용하기](https://tech.songyunseop.com/post/2016/09/seo-for-blog/)
* [Add metadata tags to Jekyll blog posts](http://jovandeginste.github.io/2016/05/18/add-metadata-tags-to-jekyll-blog-posts.html)
* [OpenGraph를 통한 썸네일 지정](https://lanace.github.io/articles/what-is-open-graph/)

전반적으로 Jekyll 블로그의 포맷을 따라야 하는 부분들이 있어, 관련 내용 및 적용기는 별도 포스팅으로 작성할 듯 싶다.



# 마무리

미루고 미루던 작업을 처리했더니 속이 다 시원하다!!!! 

효율적으로 포스팅을 작성하고 싶어서 오랫동안 사용하던 네이버 블로그를 떠나 GitHub 블로그로 옮긴건데 어째 손이 더 많이 가는 느낌이지만........ 일단 더 사용해보고 고민을 이어나가야겠다.

일단 검색엔진 등록 작업도 끝!



## 참고자료

* [Github blog 글을 구글(Google)에서 검색되도록 설정하는 방법](https://seongkyun.github.io/others/2018/12/31/google-search-enable_jekyll/)
* [[Jekyll] 검색엔진에 블로그 등록하기 _Naver편](https://gmlwjd9405.github.io/2017/10/21/include-blog-in-a-NaverSearchEngine.html)

