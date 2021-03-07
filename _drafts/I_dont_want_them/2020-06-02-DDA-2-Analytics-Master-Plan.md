---
title: "[ADsP] 데이터 분석 기획 - 2) 분석 마스터 플랜"
date: 2020-06-02 21:30  
layout: post
category: DataScience
tags:
  - DataScience
  - DataScientist
  - ADsP
comments: true


---



> ADsP를 준비하며 개인 학습용도로 정리한 자료입니다.
>
> 그림자료는 대부분 직접 제작하였으며 외부 자료인 경우에는 최대한 출처를 남겨두었습니다.
>
> 잘못되었거나 부족한 정보가 있을 수 있으니 다른 자료와 함께 참고해주시길 바랍니다.



**데이터 분석 기획과 데이터 분석 방법론에 대해 알아보자**

<!-- more -->



# 분석 마스터 플랜

* 분석 마스터 플랜 : 발굴한 분석 과제들을 우선순위별로 나열한 계획
* **마스터 플랜 수립 프레임워크**
* **분석 거버넌스 체계** : 마스터 플랜을 실행하기 위해 내부적으로 거버넌스 체계를 잡는다



## 마스터 플랜 수립 프레임워크

데이터 기반 구축을 위하여 분석 과제를 대상으로 다양한 기준을 고려해 적용 우선순위를 설정 & 로드맵 수립

* **적용 우선순위 설정 시 - 고려요소 3가지**
  * 전략적 중요도 : 전략적 필요성, 시급성
  * 비즈니스 성과/ROI
  * 실행 용이성 : 투자 용이성, 기술 용이성
* **적용 범위 / 방식 (로드맵) 수립 시 - 고려요소 3가지**
  * 업무 내재화 적용 수준
  * 분석 데이터 적용 수준
  * 기술 적용 수준
* 참고 내용
  * ISP (Information Strategy Planning, 정보 전략 계획) : 조직의 내외부 환경을 분석하여 시스템 구축 우선순위를 결정하는 등 중장기 마스터 플랜을 수립하는 절차
  * 분석 마스터 플랜 : ISP 방법론을 활용하며 데이터 분석의 특성을 고려하여 분석과제를 빠짐없이 도출
    * 과제의 우선순위 => 단/중/장기 계획 수립

### ROI 관점에서의 빅데이터 핵심 특징

> 출제포인트 : ROI 요소, 3V, 4V 내용, 평가기준과의 매칭

* 투자비용 요소 (3V) - **난이도**
  * 크기 (Volume)
  * 다양성 (Variety)
  * 속도 (Velocity)
* 비즈니스 효과 (4V) - **시급성**
  * 가치 (Value) : 데이터 분석을 통해 얻은 목표 가치

### 과제 우선순위 선정

* 시급성 : 전략적 중요도, 목표가치 (KPI)

* 난이도 : 데이터 획득 / 저장 / 가공비용, 분석 적용 비용, 분석 수준

* 포트폴리오 사분면 분석

  ![](http://www.dbguide.net/publishing/img/dbguide/bigdata_technology/511_bigdata_4.png)

  * 난이도가 낮고 시급성이 높은 것 부터 먼저 처리

    ![](http://www.dbguide.net/publishing/img/dbguide/bigdata_technology/511_bigdata_5.png)

    * 난이도 관점 : 3 -> 1 -> 2
    * 시급성 관점 : 3 -> 4 -> 2

  * 2사분면 : 가장 나중에 한다

### 로드맵 수립

데이터 분석체계 도입 -> 데이터 분석 유효성 검증 -> 데이터 분석 확산 및 고도화

* 폭포수 모델 : 모든 단계를 순차적으로 수행
* **혼합형 : 데이터 수집/확보/준비 단계는 순차적으로, 모델링 단계는 반복적으로 수행**
