---
layout: post
title: "ROS2를 Docker에서 VNC까지 띄워보기"
date: 2023-08-04
category: Robotics
tags:
  - ROS
  - Docker
comments: true
---

오랜만의 포스팅입니다 :-) 다들 잘 지내셨을까요!

저는 현재 사내 Associate Architect 과정 수강중입니다. Associate Architect 자격 취득을 위해서는 모의 프로젝트에 대한 아키텍처링을 진행하고 보고서를 제출해야하는데요. 매 차수마다 그 주제가 다른데, 이번 차수는 ROS2 기반의 로보틱스입니다! (두둥)

다른 차수의 경우에도 서비스 플랫폼, 온라인 쇼핑몰 (MSA), 머신러닝, 데이터분석 등 다양한 분야에 대한 아키텍처링을 진행한 것으로 알고 있는데요. 사실 저는 상술한 분야를 기대했는데 정말 단한번도 발을 담궈본 적 없는 로보틱스가 선정되어 잠시동안 당황했습니다ㅎㅎ

그래도 이번 기회에 아주 조금이나마 (발톱이나마...) 로보틱스를 살펴볼 수 있게 되어 좋은 것 같네요! 이렇게 또 시야를 넓혀나갈 수 있겠죠ㅎㅎ

진짜 아무것도 모르는 1인이기 때문에 조금이나마 이해해보고자 데모 프로그램을 돌리는 과정을 포스팅해보려 합니다!

그럼 시작해볼까요 :-D



<!-- more -->

# 1. Ubuntu에 Docker 설치하기

Docker Desktop 최신버전을 설치하려면 현시점(23년 8월 4일) 기준으로 Ubuntu 버전이 22.04 LTS 이거나 21.10 이어야 합니다. Ubuntu버전이 낮다면 이번 기회에 업데이트하도록 합시다!

- [참고] Docker 공식 홈페이지 Install on Ubuntu : https://docs.docker.com/desktop/install/ubuntu/

## 설치전 사전 환경 설정

### `gnome-terminal` 설치

gnome 환경이 아닌 경우라면 `gnome-terminal` 설치를 해야합니다.

Ubuntu 설치후 별다른 설정을 하지 않았다면 default가 gnome일 거긴 한데... 혹시모르니 체크해봅시다 :

```bash
$ sudo apt install gnome-terminal  
패키지 목록을 읽는 중입니다... 완료
의존성 트리를 만드는 중입니다... 완료
상태 정보를 읽는 중입니다... 완료        
패키지 gnome-terminal는 이미 최신 버전입니다 (3.44.0-1ubuntu1).
0개 업그레이드, 0개 새로 설치, 0개 제거 및 58개 업그레이드 안 함
```

이렇게 이미 최신버전이라 뜨면 당연히 설치된 것 입니다! 굿!

### Preview or Beta 버전 Docker 제거

우리는 최신 버전 Docker 를 설치할 건데... 프리뷰 버전이나 베타 버전을 사용하고 있었다면 삭제해줘야합니다. 저는 베타버전을 사용중이었어서 삭제했어요 :

```bash
$ sudo apt remove docker-desktop
$ rm -r $HOME/.docker/desktop
$ sudo rm /usr/local/bin/com.docker.cli
$ sudo apt purge docker-desktop
```

설정파일까지 싹 깨끗하게 지워줬습니다 :-)

## Docker Desktop 설치하기

### Docker의 Package Repository 셋팅하기

- [참고] set up the repository : https://docs.docker.com/engine/install/ubuntu/#set-up-the-repository

Docker Repository를 apt에 추가하고 설치해야 하는데, 그전에 Docker의 공식 GPG Key을 추가해야해요 : 

```bash
# Docker's official GPG key
$ sudo apt-get install ca-certificates curl gnupg
$ sudo install -m 0755 -d /etc/apt/keyrings
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
$ sudo chmod a+r /etc/apt/keyrings/docker.gpg 
```

위에서 만든 gpg key로 apt에 Docker Repository를 추가합시다 : 

```bash
$ echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

apt에 새로운 repository 가 추가되었으니 apt package index를 업데이트해줍시다 :

```bash
$ sudo apt-get update
```



### 최신 Docker Desktop DEB 패키지 다운로드 및 설치

- [참고] Docker Desktop Release Note : https://docs.docker.com/desktop/release-notes/

![](https://drive.google.com/uc?export=view&id=1p6yw0dOI4vmybXdBm5eFiVfTFb9wwp8d)

현시점 최신 버전은 4.22.0 버전이네요. (8월 3일에 나온 따끈따끈한...버전!)

Ubuntu는 위 링크 중에서 Debian을 선택해서 다운로드하면 됩니다. 다운로드 한 파일로 설치를 진행합시다 : 

```bash
$ sudo apt-get install ./docker-desktop-4.22.0-amd64.deb
```

설치 이후 버전을 확인해봤을 때, 아래와 같이 나오면 정상 설치 된 것입니다 :

```bash
$ docker version  
Client: Docker Engine - Community
 Version:           24.0.2
 API version:       1.43
 Go version:        go1.20.4
 Git commit:        cb74dfc
 Built:             Thu May 25 21:52:13 2023
 OS/Arch:           linux/amd64
 Context:           desktop-linux

Server: Docker Desktop 4.22.0 (117440)
 Engine:
  Version:          24.0.5
  API version:      1.43 (minimum version 1.12)
  Go version:       go1.20.6
  Git commit:       a61e2b4
  Built:            Fri Jul 21 20:35:45 2023
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.6.21
  GitCommit:        3dce8eb055cbb6872793272b4f20ed16117344f8
 runc:
  Version:          1.1.7
  GitCommit:        v1.1.7-0-g860f061
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```

# 2. Docker 셋팅하기

Docker를 실행하고 기본적인 셋팅을 해볼게요! : 

```bash
$ systemctl --user start docker-desktop
```

Docker는 비회원 상태로도 사용할 수 있긴하지만, 기왕하는거 계정을 만들도록 합시다.

참고로 계정을 만드려면, 아래와 같이 gdg public key세팅을 해야합니다! : 

https://docs.docker.com/desktop/get-started/#sign-in-to-docker-desktop

저는 이미 있어서 패스했습니다 :-)

## 부팅시 자동 실행

계정 로그인 후 설정으로 들어가서 Ubuntu 부팅시에 Docker도 자동으로 시작하도록 설정해줍시다 : `Settings` > `General` > `Start Docker Desktop when you log in`  체크!

![](https://drive.google.com/uc?export=view&id=1UbbzYMUUhNlGhtlBRO_gDrILhjPPsS8g)

## Docker 이미지 다운로드 위치 설정

Docker 이미지들은 용량을 꽤나 차지하는 편이라, 다운로드 위치를 적절하게 설정해야 디스크가 꽉차는 슬픈 사태를 방지할 수 있습니다.

Docker Image Default 저장 위치는 `/var/lib/docker` 입니다 : 

```bash
$ docker info | grep "Docker Root Dir"
Docker Root Dir: /var/lib/docker
```

위치를 변경하기 위해서 일단 실행중인 docker 를 중지시켜야해요 : 

```bash
$ systemctl stop docker
```

아래와 같이 daemon.json 파일에 변경할 위치를 적어줍시다 : 

```bash
$ vi /etc/docker/daemon.json
{
        "data-root": "변경할 Docker 이미지 저장 위치"
}
```

docker 를 다시 실행시키고 위치가 잘 변경되었는지 확인해보세요 (저는 변경한 위치가 루트 권한이 있어야 접근 가능한 위치라 sudo를 입력해줬습니다) :

```bash
$ systemctl start docker
$ sudo docker info | grep "Docker Root Dir"
 Docker Root Dir: 변경한 위치
```



# 3. ROS2 설치하고 실행시켜보기

이제 기본적인 세팅은 다 되었으니 ROS2 VNC docker 이미지를 땡겨옵시다 : 

```bash
$ sudo docker pull tiryoh/ros2-desktop-vnc:foxy
foxy: Pulling from tiryoh/ros2-desktop-vnc
.....
Status: Downloaded newer image for tiryoh/ros2-desktop-vnc:foxy
docker.io/tiryoh/ros2-desktop-vnc:fox
```

위와 같이 설치가 완료되고나면 이미지를 실행시켜보아요 (참고로 8080포트는 자주 사용될 수 있는 포트라 좀 특이한 포트번호로 실행하는게 더 좋은 것 같습니다. 8080 개발용 포트로 많이쓰다보니..ㅎ 나중에 겹치면 귀찮으니까요...) : 

```bash
$ sudo docker run -it -p 8080:80 --name ros tiryoh/ros2-desktop-vnc:foxy
* enable custom user: ubuntu
  set default password to "ubuntu"
2023-08-05 15:17:35,895 INFO Included extra file "/etc/supervisor/conf.d/supervisord.conf" during parsing
2023-08-05 15:17:35,895 INFO Set uid to user 0 succeeded
2023-08-05 15:17:35,899 INFO RPC interface 'supervisor' initialized
2023-08-05 15:17:35,899 CRIT Server 'unix_http_server' running without any HTTP authentication checking
2023-08-05 15:17:35,899 INFO supervisord started with pid 44
2023-08-05 15:17:36,904 INFO spawned: 'novnc' with pid 46
2023-08-05 15:17:36,911 INFO spawned: 'vnc' with pid 47
2023-08-05 15:17:38,127 INFO success: novnc entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2023-08-05 15:17:38,127 INFO success: vnc entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
```

위와 같이 출력되고나면 웹 브라우저에 `localhost:8080` 을 입력하여 진입해봅시다 :

![](https://drive.google.com/uc?export=view&id=1VUMln-ii4ryJv03oSlJhx7MVzD1b3dsv)

여기서 연결 버튼을 클릭하여 진입해보면 ubuntu 이미지 홈 화면이 보여질 겁니다! 그럼 성공! :

![](https://drive.google.com/uc?export=view&id=1cJW7kK7iJWPWQY0i4l9kRi-pTvz4ie7T)



# 4. Demo 실행해보기

ROS2 에서는 학습용으로 Demo 프로그램을 제공해줍니다. 아래 공식 사이트를 참고하여 데모를 실행시켜봤습니다 : 

https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Introducing-Turtlesim/Introducing-Turtlesim.html

## turtlesim

먼저 귀여운 `turtlesim` 이라는 시뮬레이션 데모 프로그램을 실행시켜보겠습니다!

브라우저로 실행시킨 이미지의 좌측 상단 Menu를 클릭하여 Terminator 를 실행시켜줍니다. Terminator는 Terminal 창을 분할하여 사용할 수 있어 매우 편리하죠!

![](https://drive.google.com/uc?export=view&id=1FmIl3-VW5qi5rafdJqTdLxbVtHOkkrC0)

Terminator에 아래 명령을 입력하여 시뮬레이터를 실행시켜봅시다 : 

```bash 
$ ros2 run turtlesim turtlesim_node
```

![](https://drive.google.com/uc?export=view&id=1ILVIm1Hgj-5Kf4mLSqSBnzDka0QQGc-Q)

그럼 이렇게 귀여운 거북이가 나타납니다ㅎ

이건 정말 시뮬레이터를 실행만 시킨 것이라.. 창을 하나 더 띄워 거북이를 조종해볼게요 :

```bash
$ ros2 run turtlesim turtle_teleop_key
```

![](https://drive.google.com/uc?export=view&id=1nKvooCDrvl4vg6Gh4NkO_p0l28oTNkyz)

그럼 위와 같이 G, B, V, C, D, E, R, T 키로 거북이를 회전시킬 수 있다는 설명이 표시됩니다.

C를 눌러보니 아래와 같이 거북이 좌측 하단 방향으로 회전하네요. (귀엽다..)

![](https://drive.google.com/uc?export=view&id=1xUE0QbdJSyHcyYKAMu8rAan7TCUqyTS9)

그리고 키보드 상하좌우 키를 이용하면 거북이가 하얀선을 그리면서 이동도 합니다ㅎ (귀엽..2)

이렇게 거북이를 조종할 때, 이벤트가 어떻게 전달되고 어떻게 실행되는지에 대한 간략한 상태도를 확인해볼 수 있어요. 창을 하나 더 띄워 확인해봅시다 : 

```bash
$ rqt_graph
```

![](https://drive.google.com/uc?export=view&id=1ctXBeRL8bG-p4yo4eeC8TFpF49lUfx3j)

대강 살펴보니 teleop_turtle이 방향 전환 command를 turtlesim에게 전달하면 turtlesim은 teleop_turtle에게 feedback과 현재 status를 응답해주는 흐름으로 진행된다는 뜻인 것 같습니다.

rqt_graph 창에서 `Nodes only` 를 `Nodes/Topics (active)` 로 변경해보면 현재 어떤 Topic이 쓰이고 어떻게 메세지가 이동하는지도 보여지는데, 이걸 제대로 이해하기 위해서는 Topic, Node 에 대한 학습이 별도로 필요해보이네요!

![](https://drive.google.com/uc?export=view&id=1Pz5bU1-buArb9yGsTfn2SUxxjhBbA0jJ)

## talker & listener

채팅 프로그램처럼 한쪽에서 말하면 다른쪽에서 이걸 리스닝하는 데모 프로그램도 있습니다. 이번엔 이걸 돌려볼게요!

Terminator의 창을 두개 띄워서 한쪽에는 `ros2 run demo_nodes_cpp talker` 를, 다른 한쪽에는 `ros2 run demo_nodes_cpp listener` 를 입력해봅시다.

talker는 계속 Hello World! 를 보내고, listener는 이를 수신할 겁니다.

이 데모도 상태도로 한번 확인해보면 아래와 같이 출력되네요 : 

![](https://drive.google.com/uc?export=view&id=1xHlU1OYZ_NIWZDtiM_9QW0fguqfS24uD)

talker가 chatter로 메세지를 보내면 listener가 이를 수신하는 방식으로 진행되고있다는 것 같아요! 이렇게 그래프로 전체 흐름을 한눈에 볼 수 있으니 진짜 좋은 것 같습니다 :-)

# 5. ROS2 rqt_graph 조금이나마 이해해보기

사실 일단 무턱대로 데모 프로그램을 돌려본 거라 완벽한 이해를 하기엔 어려웠어요...

대략적으로라도 이해해야 아키텍처링 연습을 할 수 있기 때문에 공식사이트 문서를 살펴보기로 했습니다.

- Understanding nodes : https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Nodes/Understanding-ROS2-Nodes.html
- Understanding topics : https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Topics/Understanding-ROS2-Topics.html
- Understanding services : https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Services/Understanding-ROS2-Services.html

## ROS2의 오버뷰

![](https://docs.ros.org/en/foxy/_images/Nodes-TopicandService.gif)

아직 잘은 모르지만.. ROS2는 크게 Node, Service, Topic으로 구성되는 것 같아보여요. Node간의 커뮤니케이션 수단으로 Service와 Topic이 이용되는 것으로 보입니다. Topic은 일종의 채널로서  Publisher Node에서 Subscriber Node로의 메세지 전달을 해주는 단방향 채널로 보이며, Service는 말그대로 서비스.. Client <-> Server 간의 메세지를 전달하는 양방향 채널로 보이네요.

이제 좀 데모 프로그램에서 띄워봤던 상태도가 이해되기 시작합니다 :-)



# 마무리

일단은 오늘의 목적은 세팅이었으니 여기까지만 하겠습니다! 다음 시간에는 Node, Topic, Service에 대해 자세히 학습해보도록 하겠습니다! (시간관계상 포스팅을 작성할 수 있을지는 모르겠네요ㅠㅠ 올릴 수 있으면 올려보겠습니다!)

간단하게 시뮬레이터를 돌려본 소감은... `아직까지는 재밌다!` 싶네요ㅎ 겉핥기만 했기 때문이겠죠!

저는 작은 기회가 주어졌을 때, 작게 처리하고 넘기기보다는 그 기회를 백분 활용하여 100%, 200% 딥다이빙해보는 걸 선호하는 편입니다. 인증 취득 관점에서는 좀 비효율적일 수는 있겠지만 이렇게 해야 인증 뿐만 아니라 실제 응용력까지 생겨 결론적으로는 교육의 효과가 더 커지는 것 같더라구요.

그런 의미에서 이번 기회에 ROS2도 즐겁게 살펴보려합니다. 관련 서적도 주문했고요ㅎ 재밌겠네요!

화이팅!
