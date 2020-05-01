---
title: "recvfrom() with time-out checking"
date: 2012-06-11 01:15
layout: post
category: Operating System
tags:
  - TIL
  - Network
  - 스크랩
comments: true
---

* 참조 : http://blog.phamansinh.com/2008/08/10/recvfrom-with-time-out-checking/

<!-- more -->



----



> 이 포스팅은 기존 개발 블로그에서 백업한 포스팅입니다.
>
> * 원문 : https://syung1104.blog.me/159638635



----



우리가 일반적으로 사용하는 Network 프로토콜중 UDP로 부터 데이터를 받는 함수가 recvfrom()이다. 

이함수는 네트워크로 부터 메시지가 들어올때까지 대기한다.

– 메시지가 안들어오면?.. 들어올때 까지 대기한다. 끝까지… 사용자가 종료하기 전에는 쭈욱 기다리는 것이다.



**해결 1. select()**

recvfrom 이 호출되면 무엇인가 받을 때 까지 대기한다고 했다. 

그럼 해결방법은 무엇인가 들어올때 recvfrom을 호출해 주면 된다. 

그와 같은 일을 해주는 것이 **select 함수**이다. timeout 이란 것이 있어서 기다리는 시간을 설정할수 있다. 

timeout 만큼 기다려서 들어오지 않으면 도착하지 않은것으로 판별하면 된다. 

그전에 데이터가 도착한다면 특정함수를 호출해주면 된다. 

우리는 데이터를 가져오기 위한 recvfrom를 호출하는 것이다. 



[![img](http://cfile2.uf.tistory.com/image/120D1B0F4A1B36AE14E16D)](http://cfile24.uf.tistory.com/image/143916284A1B36AE36FA1D)



manpage의 내용을 좀더 적어 보면? 
\- select 는 상태가 변경되는 파일 기술자들의 숫자를 기다린다.

참조 페이지에 있는 예제 소스를 가져와 보겠다. (외국 블로그라 영어로, 코드가 원래 영어지만)

```c
int recvfromTimeOut(SOCKET socket, long sec, long usec)
{
 // Setup timeval variable
 timeval timeout;
 timeout.tv_sec = sec;
 timeout.tv_usec = usec;
 // Setup fd_set structure
 fd_set fds;
 FD_ZERO(&fds);
 FD_SET(socket, &fds);
 // Return value:
 // -1: error occured
 // 0: timed out
 // >0: data ready to be read
 return select(0, &fds, 0, 0, &timeout);
}
res = recvfromTimeOut(s, 10, 0);
switch (res)
{
case 0:
 // Timed out, do whatever you want to handle this situation
 break;
case -1:
 // Error occured, maybe we should display an error message?
 break;
default:
 // Ok the data is ready, call recvfrom() to get it then
 recvfrom(s, buf, 1024, 0, (sockaddr *)&addr, &fromLen);
}
```

나는 recvfromTimeOut 안에서 recv 까지 사용할 생각을 했다. 

그런데 ? 그럼 return에 대한 문제가 발생할듯하다. 

recvfrom의 원래 return 값과, timeOut에 의한 return값이 중복이 될듯하다.

 

**해결 2. non-blocking I/O**

간다한 해결법으로 recvfrom을 안기다리도록 만들면 되는것 아닌가?

blocking I/O 방식이기 때문에 recvfrom은 무한정 대기하는 것이다. 그럼 non-blocking I/O 방식으로 recvfrom를 만드는 것이다. 소켓의 설정(?)에 그와 같은것이 들어 있다.

```c
// Set our socket to non-blocking mode using ioctlsocket() function
u_long iMode = 1;
if (ioctlsocket(s, FIONBIO, &iMode))
{
 cout<<"ioctlsoket failed"<<endl;
 return 1;
}
```



[![img](http://cfile25.uf.tistory.com/image/20390C284A1B36AF392AE9)](http://cfile22.uf.tistory.com/image/1468E0114A1B36AF37BB96)

위와 같이 설정을 하게 되면 recvfrom은 무조건 return 하게 된다.

```c
endTime = clock() + 5000;

while (recvfrom(s, buf, 1024, 0, (sockaddr *)&addr, &fromLen) == -1 && clock() < endTime) { }
```

위와 같은 코드로 변경하여 recvfrom 이 –1을 리턴하고 endTime이 안되었으면 계속 반복하는것이다.

이것은 무한 루프처럼 계속 반복된다는 단점이 있다.

그래서 1번 방법을 더 추천한다.

* 출처 : http://log.bestf.net/136



| > 내 생각!                                                   |
| ------------------------------------------------------------ |
| 참조 블로그에 있는 내용을 그대로 가져왔다<br/>한글로 그리고 내가 적고 싶은 방법으로 바꾸었지만 원본에 추가된 내용이 별로 없는듯 하다. |


