---
title: "[Android] 허니컴(3.0) 이후 TabActivity가 Deprecated 되었다"
date: 2012-07-02 02:52
layout: post
category: Android
tags:
  - Android
  - Honeycomb
  - Update
  - Deprecated
comments: true
---



<!-- more -->



----



> 이 포스팅은 기존 개발 블로그에서 백업한 포스팅입니다.
>
> * 원문 : https://syung1104.blog.me/161046481



----





허니컴(3.0)부터는 Fragment 클래스들을 제공하여 Tab이나 Group Activity등을 Fragment로 관리하게 해준다고한다.

하위버전에서 제공하던 TabActivity나 ActivityGroup같은 클래스는 사용하지 않는 것을 권장하고 있다.

 ![img](https://github.com/yenarue/images/blob/master/Android/deprecated_tabactivity.jpeg?raw=true) 

실제로 Android SDK와 Eclipse를 최신버전으로 업그레이드 한 뒤

안드로이드 코딩을 하다보니 TabActivity와 같은 경우는 Deprecated되어 절취선?취소선? 같은 것이 그어지며 사용하지 않기를 권장하고 있다.

분명히 멀쩡한 코드인데 4.0.3 에뮬에서 에러가 뜨는 것으로보아 몇몇은 아예 기능을 없앤듯도 싶다...

* Fragment관련 클래스에 대한 안드로이드 개발자센터 페이지 : http://developer.android.com/sdk/compatibility-library.html



 ....

오랜만에 안드로이드 개발에 들어가게 되어서 

관련책을 구해 이것저것 보면서 코딩하는데

최신버전으로 업그레이드 해서 그런지 영 어색하고 답답하다;;;

으 잘할 수 있을까 걱정이 태산이다..