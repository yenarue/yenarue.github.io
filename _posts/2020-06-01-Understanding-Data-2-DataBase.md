---
title: "데이터의 이해 - 2) 데이터베이스 (정의/특징/활용)"
date: 2020-06-01 22:45  
layout: post
category: DataScience
tags:
  - DataScience
  - DataBase
  - ADsP
comments: true
---



> ADsP를 준비하며 개인 학습용도로 정리한 자료입니다.
>
> 그림자료는 대부분 직접 제작하였으며 외부 자료인 경우에는 최대한 출처를 남겨두었습니다.
>
> 잘못되었거나 부족한 정보가 있을 수 있으니 다른 자료와 함께 참고해주시길 바랍니다.



<!-- more -->



# 데이터베이스

### 연혁

* 1950년대 :  **미군에서 군비상황을 관리**하기 위해 **데이터(data)의 기지(base)**를 설립함 
* 1975년 : **우리나라에서 데이터베이스 이용이 시작**됨
* 1980년대 중반 : 국내의 데이터베이스 관련 기술 연구/개발
  * 경영정보시스템으로 이용하기 시작함

## 데이터베이스의 개념, 정의

네트워크와 빅데이터 시대를 지나며 개념과 정의가 확대되기 시작함

### 최초 개념

체계적, 조직적으로 정렬된 데이터 집합을 의미

### 1차 개념 확대 - 정형 데이터 관리

* 대용량의 데이터를 저장/관리/검색/이용할 수 있는 컴퓨터 기반의 데이터베이스

### 2차 개념 확대 - 비정형데이터 포함

* 문자, 기호, 음성, 화상, 영상 등 다수의 콘텐츠를 체계적으로 수집/축적하여 다양한 용도와 방법으로 이용할 수 있도록 정리한 정보의 집합체 

## 데이터베이스의 특징

### 일반적 특징

* **통합된 데이터 (Integrated Data) :** 동일한 내용의 데이터가 중복되어 있지 않음
* **저장된 데이터 (Stored Data) :** 데이터가 저장매체에 저장됨
* **공용 데이터 (Shared Data) :** 여러 사용자가 서로 다른 목적으로 공동으로 이용
* **변화되는 데이터 (Changable Data) :** CRUD. 항상 변화하면서도 현재의 정확한 데이터를 유지

### 다양한 측면에서의 특징

* **[중요] 정보의 축적 및 전달 측면**
  * 기계가독성 : 컴퓨터 등의 기기가 읽고 쓸 수 있다
  * 검색가독성 : 다양한 방법으로 필요한 정보를 검색한다
  * 원격조작성 : 정보통신망을 통해 원거리에서도 즉시 이용 가능하다
* 정보 이용 측면 : 다양한 정보를 정확하고 경제적으로 신속하게 획득
* 정보 관리 측면 : 방대한 양의 정보를 체계적으로 축적, 추가, 갱신 용이
* 정보기술 발전 측면 : 기술의 발전을 견인
* 경제/산업 측면 : 정보를 신속하게 제공/이용할 수 있는 인프라 특성을 가짐 => 경제/산업 발전에 기여



## 데이터베이스의 활용

### 기업내부 데이터베이스

기업 경영 전반에 관한 데이터를 연계하여 일관된 체계로 구축, 운영하는 경영활동의 기반이 되는 전사시스템

#### 1980년대

* OLTP (Online Transaction Processing) : 호스트 컴퓨터가 데이터베이스에 엑세스하고 바로 처리 결과를 돌려주는 형태
* OLAP (Online Analytical Processing) :  다양한 비즈니스 관점에서 쉽고 빠르게 **다차원적인 데이터에 대화식으로** 접근하여 의사결정에 활용할 수 있는 정보를 얻을 수 있게 주는 기술

![](https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FkQyy4%2FbtqwrqVhVhp%2FlhQsHjGi3YdiGGAZX6kNJk%2Fimg.jpg)

#### 2000년대

* CRM (Customer Relationship Management, 고객 관계 관리) : 기업과 **고객과 관련된 내/외부 자료**를 분석/통합하여 **고객특성에 맞게 마케팅 활동**을 계획/지원/평가하는 과정
* SCM (Supply Chain Management, 공급망 관리) : 원재료의 생산에서부터 고객에게 유통하는 공급망의 단계까지, **모든 단계에 걸쳐 정보들을 공유하며 원활하게 제품을 생산하고 공급**하는 시스템
* ERP (Enterprise Resource Planning, 전사적 자원 관리) : 경영자원을 하나의 통합 시스템으로 재구축
  * ![](https://lh3.googleusercontent.com/proxy/D71DkU8DYGkkUvubAWHTASquCzsV_rd6sKB1Ju0Bsxlu9bnINnG-psdvxbx1dL7izwdprFJa5cXmRBHdnNiv70VlTEcxZ8ducyGjPvG1K-Jg6_Gk)

* BI (Business Intelligence, 비즈니스 인텔리전스) : 기업의 수많은 데이터를 정리/분석하여 **기업의 데이터 기반 의사결정에 활용**하는 일련의 프로세스 및 **도구**
  * 질의(query), 보고(reporting), 온라인 분석처리(OLAP), 통계분석, 예측, 데이터마이닝 등의 결합이다.
  * BA (Business Analytics) : BI에 쓰이는 분석 툴(**기법**)들



### 분야별 데이터베이스

1. 제조
   * 2000년을 기점으로 전환
   * 클라이언트/서버 기반의 내부 정보 시스템 -> 웹 전환
   * ERP -> SCM 대기업 위주의 발전
   * RTE (Real-Time Enterprise) 을 통한 협업적 IT 화 비중 확대
2. 금융
   * 2000년대 초반
     * EAI (Enterprise Application Integration) : 정보를 중앙집중적으로 통합, 관리, 사용할 수 있는 시스템
   * 2000년대 중반
     * EDW (Enterprise Data Warehouse) : DW(Data Warehouse)를 전사적으로  확장하여 다양한 분석 애플리케이션을 위한 원천
3. 유통
   * 충성도 높은 고객들을 유치 : CRM
   * 빠르고 효율적인 물건 공급 : SCM
   * KMS (Knowledge Manager System, 지식 관리 시스템) : 기업경영을 지식이라는 관점에서 새롭게 조명함
   * RFID : RFID 태그를 이용하여 빠른 정보 인식

