---
title: "[ADsP] 데이터 분석 기획 - 1) 분석 기획과 방법론"
date: 2020-06-02 20:00  
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

# 2과목. 데이터 분석 기획

* 데이터 분석 기획
  * 데이터 분석 기획 방향성 도출
  * 분석 및 분석과제발굴 방법론
  * 분석 프로젝트 관리 방안

* 분석 마스터 플랜
  * 마스터 플랜 수립 프레임워크
  * 분석 거버넌스 체계



# 데이터 분석 기획

* 분석 프로세스
  * 정량적 데이터 분석 프로세스
  * 빅데이터 분석 프로세스
* 분석 과제 발굴

# 분석 기획

실제 분석을 수행하기 앞서, 분석을 수행할 **과제의 정의에서부터 의도했던 결과를 도출하기 까지의 과정을 적절하게 관리할 수 있도록 방안을 사전에 계획**하는 일련의 작업

* 어떠한 목표(what)를 위해(why) 어떤방식으로(how) 수행할지에 대한 일련의 계획

## 분석의 유형

**분석 대상(What)**과 **분석 방식(How)**에 따라 4가지로 나뉜다

![](https://wikidocs.net/images/page/48087/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B72.jpg)

* **최적화 (Optimization)** : Known, Known
  * 분석 대상, 분석 방법을 모두 알고 있는 경우
* **통찰 (Insight)** : Unknown, Known
  * 분석 방법은 알지만 분석 대상이 무엇인지 인지하지 못하는 경우
* **솔루션 (Solution)** : Known, Unknown
  * 분석 대상은 알지만 분석 방법을 모르는 경우
* **발견 (Discovery)** : Unknown, Unknown
  * 분석 대상과 분석 방법을 모두 모르는 경우

## 목표 시점별 분석 기획

> 출제포인트 : 목표 시점 별 방향, 목표, 유형, 접근 방식에 대한 특징

* **과제 중심적인 접근 방식** : 당면한 과제를 빠르게 해결 & 단기적인 접근 방식
  * 1차 목표 : Speed & Test
  * 과제의 유형 : Quick-Win
  * 접근 방식 : Problem Solving
* **장기적인 마스터 플랜 방식** : 지속적인 분석 내재화 & 중장기적인 접근 방식
  * 1차 목표 : Accuracy & Deploy
  * 과제의 유형 : Long Term View
  * 접근 방식 : Problem Definition

## 분석 기획시 주의 사항

* 가용데이터에 대한 고려 (Available Data) : 적절한 데이터를 사용하고 있는가?

  * 데이터 유형에 따라 솔루션, 분석 방법이 달라질 수 있음
  * 정형 데이터, 반정형 데이터, 비정형 데이터 (관련 내용은 1과목에 정리해둔 내용이 있다. 그것을 참고하기!)

* 적절한 활용 방안과 유즈케이스 탐색 (Proper Business Use Case)

  * 벤치마킹을 빠르게 하는 것이 좋다 => 실패할 확률을 줄인다

* 장애요소들에 대한 사전 계획 수립 (Low Barrier of Execution)

  * 조직 문화 내재화, 계속적인 교육, 변화 관리 (change management)

    

# 분석 방법론 (분석 프로세스)에 대하여

데이터 분석이 효과적, 문화적으로 정착하기 위해서는 **체계화된 절차와 방법이 정리된 분석 방법론 수립**이 필수적이다

* 절차 (Procedures), 방법 (Methods), 도구와 기법 (Tools&Techniques), 템플릿과 산출물 (Templates&Outputs)

## 데이터 기반 의사결정

  * 경험과 감에 의한 결정보다는 **데이터 기반의 의사결정을 하는 것이 합리적**이다.
  * **장애요소 : 고정관념 (Sterotype), 편향된 생각 (Bias), 프레이밍효과 (Framing Effect)**
    * 프레이밍 효과 : 동일 사건/상황에 대해 표현하는 방식에 따라 판단이 달라질 수 있는 현상

## 방법론 모델

![출처 : https://multicore-it.com/45](https://img1.daumcdn.net/thumb/R720x0.q80/?scode=mtistory2&fname=http%3A%2F%2Fcfile21.uf.tistory.com%2Fimage%2F9911C44B5BE9B1242EFC45)

* 폭포수 모델 (Waterfall Model) : 순차적으로 진행
* **프로토타입 모델 (Prototype Model) : 점진적 개발 모델 - 일부분 먼저 개발 -> 개선**
* 나선형 모델 (Spiral Model) : 반복을 통해 점증적으로 개발
  * 초기 프로젝트에 적용이 용이 / But, 관리체계를 체계적으로 갖추지 못한 경우에는 오히려 복잡도가 상승하여 프로젝트 진행이 어려울 수 있음

## 방법론 구성

방법론은 계층적으로 구성된다

**단계 -> 태스크 -> 스탭**

* 단계 : 단계별 산출물이 생성

  * output : 단계별 완료보고서

* 태스크 : 단계를 구성하는 단위 활동

  * output : 보고서

* 스텝 : WBS의 워크 패키지

  * output : 보고서 구성요소

    

# 분석 방법론 종류를 알아보자

![](/Users/yenarue/OneDrive/Developer/TIL/DataScience/ADsP/images/analytsis_methods_overview.png)

전반적인 방법론 플로우가 각 방법론에서는 어디에 매칭되는지 비교하면서 학습해보자

> 출제 포인트 : KDD 분석 방법론 vs CRISP-DM 분석 방법론

## 분석 방법론 1. KDD 분석 방법론

![](/Users/yenarue/OneDrive/Developer/TIL/DataScience/ADsP/images/kdd.png)

1. 데이터셋 선택 (Selection)
   * 개요 : 비즈니스 이해, 데이터 이해
2. 데이터 전처리 (Preprocessing)
   * 개요 : 데이터 전처리
3. 데이터 변환 (Transformation)
   * 개요 : 데이터 변수 생성, 데이터 분할, 데이터 변수 선택
4. 데이터 마이닝 (Data Mining)
   * 개요 : 모형 개발 (모델링)
5. 결과 평가 (Interpretation / Evaluation)
   * 개요 : 모형 평가, 모형 검증
   * 평가 후 앞단계로 다시 되돌아가서 성능을 올리기 위해 흐름을 반복한다

## 분석 방법론 2. CRISP-DM 분석 방법론

주요 5개 업체들이 주도하여 만든 계층적 프로세스 모델

> 출제 포인트 : 4가지 레벨, 6단계 프로세스, 각 단계별 업무내용, KDD와의 비교

### 4레벨 구조

![](/Users/yenarue/OneDrive/Developer/TIL/DataScience/ADsP/images/kdd-4level.png)

* 기존 방법론들 : Phase -> Task -> Step/Instance (3단계)
* CRISP-DM : Phase -> Generic Tasks -> Specialized Tasks -> Process Instances (4단계)

### 프로세스

6단계로 구성, 단방향X, 단계간 피드백을 통해 완성도를 향상시킨다

![](/Users/yenarue/OneDrive/Developer/TIL/DataScience/ADsP/images/crisp-dm.png)

* 업무 이해 (Business Understanding)
  * 개요 : 비즈니스 이해
  * 업무 목적 파악, 목표 설정, 계획 수립
* **데이터 이해 (Data Understanding)**
  * 개요 : 데이터 이해,  데이터 전처리 중 이상치 식별작업
  * 데이터 수집, 데이터 기술 분석, 데이터 탐색, 데이터 품질 확인
* **데이터 준비 (Data Preparing)**
  * 개요 : 데이터 전처리, 데이터 변수 생성, 데이터 분할, 데이터 변수 선택
  * 데이터 셋 선택, 데이터 정제, 데이터 셋 편성, 데이터 통합, 데이터 포맷팅
* **모델링 (Modeling)**
  * 개요 : 모델 개발, **모델 평가**
  * 모델링 기법 선택, 모델 테스트 계획 설계, 모델 작성, 모델 평가
* **평가 (Evaluation)**
  * 개요 : 모형 검증
  * 분석 결과 평가, 모델링 과정 평가, 모델 적용성 평가
* 전개 (Deployment)
  * 전개 계획 수립, 프로젝트 종료 보고서 작성, 프로젝트 리뷰



## 분석 방법론 3. 빅데이터 분석 방법론

> 출제포인트 : 3단계 계층, 5단계 프로세스 & 각 단계별 주요 업무 
> 시험에 자주 출제됨. 근데 너무 외울게 많아서 중요한 것들만 확인하고 패스하는게 이득일수도 있겠다. 

### 3단계 계층

![](/Users/yenarue/OneDrive/Developer/TIL/DataScience/ADsP/images/bigdata-analysis-process.png)

### 5단계 프로세스

> 출제포인트 : 가끔 세세한 스텝까지 물어보기도 함.
> 내 생각에는 이런 스텝까지 다 외우기는 힘들 듯... 어차피 실무와 큰 관련은 없으니 패스하는게 나을 듯

![](/Users/yenarue/OneDrive/Developer/TIL/DataScience/ADsP/images/bigdata-analysis-process-5.png)

* 분석 기획

  * 비즈니스 이해 및 범위 설정
  * 프로젝트 정의 및 계획 수립
  * 프로젝트 위험계획 수립

* 데이터 준비

  * 필요 데이터 정의
  * 데이터 스토어 설계
  * 데이터 수집 및 정합성 점검

* 데이터 분석

  * 분석용 데이터 준비
  * 텍스트 분석
  * 탐색적 분석
  * 모델링
  * 모델 평가 및 검증
  * 모델 적용 및 운영 방안 수립

* 시스템 구현

  * 설계 및 구현
  * 시스템 테스트 및 운영

* 평가 및 전개

  * 모델 발전 계획 수립
  * 프로젝트 평가 및 보고

  

# 분석 과제 발굴 방법론

* 분석 과제 도출 방법 : 상향식 (Bottm-Up), 하향식 (Top-Down)
  * 최적의 의사결정 : 두 접근 방식이 상호보완관계에 있을 때

![](https://wikidocs.net/images/page/48087/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B72.jpg)

* **하향식 접근 방식 (Top-Down Approach)** : 문제의 해법을 찾기 위해 **각 과정이 체계적으로 단계화 되어 수행**되는 방식
  * 분석 대상을 알고있는 경우
  * 전통적으로 수행되었던 분석 과제 발굴 방식

* **상향식 접근 방식 (Bottom-Up Approach)** : 문제의 정의 자체가 어려워 **데이터를 기반으로 문제의 재정의 및 해결방안을 탐색하고 이를 지속적으로 개선**하는 방식
  * 분석 대상을 모르는 경우



## 분석 과제 발굴 방법론 1. 하향식 접근법 (Top Down Approach)

![](/Users/yenarue/OneDrive/Developer/TIL/DataScience/ADsP/images/finding-analysis-subject-top-down-approach.png)

분석 대상이 무엇인지 알고있는 경우 이에 대한 해법(How)을 찾기 위해서 각 과정을 단계적으로 수행하는 방식

* 분석적으로 사물을 인식하려는 **Why 관점**에서 접근

### 1단계. 문제 탐색 (Problem Discovery)

* 문제를 해결함으로써 발생하는 가치에 중점을 두는 것이 중요

* **비즈니스 모델 캔버스**를 활용

  * 문제 발굴 : 업무, 제품, 고객

  * 관리 : 규제와 감사, 지원 인프라

* **분석 기회 발굴의 범위 확장**

  * 거시적 관점 : 사회, 기술, 경제, 환경, 정치
  * 경쟁자 확대 : 대체제, 경쟁자, 신규 진입자
  * 시장 니즈 탐색 : 고객, 채널, 영향자들
  * 역량의 재해석 : 내부역량, 파트너 네트워크

* 외부 참조 모델 기반 문제 탐색 (벤치마킹) : Quick & Easy

* 분석 유즈 케이스 (Analytics Use Case) 표기

### 2단계. 문제 정의 (Problem Definition)

비즈니스적인 표현을 되어있는 문제를 데이터 분석의 문제로 변환하여 정의하는 단계

* 목적 : 필요한 데이터 및 기법(How)을 정의하기 위함
* 예시 (비즈니스 문제 -> 분석 문제)
  * "고객 이탈의 증대" -> "고객 이탈에 영향을 미치는 요인을 식별하고 이탈가능성 예측"
  * "예상치 않은 설비 장애로 인한 판매량 감소" -> "설비의 장애를 이끄는 신호를 감지하여 설비 장애 용인으로 식별하고 장애 발생 시점 및 가능성을 예측"

### 3단계. 해결방안 탐색 (Solution Search)

정의된 **데이터 분석 문제 해결을 위한 다양한 방안**을 모색

![](https://lh3.googleusercontent.com/proxy/b8eDFtKUpuO1U4-UPWDW1eQG3FDCtTew9ub5evaGyOqD3UOsLPx6_6JIRH2Ao6-mx121ByYL6GFMYLnbnrb4xROxXca0ZjdFBc4GUCUwBcCSw_fIJKvYjfETTEiAR8-FJMx-iXT1oikz_Aw-UwqvQrROyHQ-AP1fmqGrKRDr4MlEEFKpksHXA3WOpSVn0pe2XAOj3WI5JEv53a8bT_Y7gsmq9Q1rTqIcuBU3H6LXDe_FUO26NqzH1PJjDG8SXJmd9vYkbkjoZ7IPbqS_sl03VE83fZh_FXGjkPFXGw)

### 4단계. 타당성 검토 (Feasibility Study)

실제로 비즈니스에 유용한지 아닌지 타당성을 검토

* 경제적 타당성 : 비용 대비 편익
* 데이터 타당성 : 데이터 존재 여부
* 기술적 타당성 : 분석 시스템 환경, 분석 역량



## 분석 과제 발굴 방법론 2. 상향식 접근법 (Bottom Up Approach)

보유하고 있는 다양한 원천데이터로부터의 분석을 통해 통찰력과 지식을 얻는 방법

문제 정의 자체가 어려운 경우 데이터를 기반으로 문제를 지속적으로 관찰하고 개선하는 방식

주로 비지도 학습방법으로 수행된다

* 사물을 있는 그대로 인식하는 **What 관점**에서 접근

### 디자인 사고 (Design Thinking)

상향식 접근 방식의 발산 단계와 하향식 접근 방식의 수행 단계를 반복적으로 수행하는 상호보완적인 방법

=> 분석의 가치를 올리는 최적의 의사결정 방식

* 프로세스 : **감정이입** -> 정의 -> 아이디어도출 -> 시제품 -> 테스트
  * "감정이입" 단계가 가장 중요하다

### 프로토타이핑 접근법

일단 분석을 시도해 보고 그 결과를 확인해 가면서 반복적으로 개선해 나가는 방법 => 시행 착오를 통한 문제 해결

* 빅데이터 분석 환경에서 프로토타이핑의 필요성

  > 가끔 출제됨

  * 문제에 대한 인식 수준 향상시키기 위해
  * 필요 데이터 존재 여부의 불확실성을 해결하기 위해
  * 데이터 사용 목적의 가변성 : 데이터를 재검토하여 사용목적과 범위를 확대할 수 있음

### 분석 과제 정의

분석 과제 정의서로 내용을 정리한다

* 분석 과제 정의서 : 소스데이터, 분석방법, 데이터 입수/분석의 난이도, 수행주기, 분석과정 등을 정의
  * 프로젝트 방향 설정, 성공여부 판별의 주요자료

# 분석 프로젝트 관리 방안

## 5가지 주요 영역

* 데이터 양 (Data Size)
* 데이터 복잡성 (Data Complexity)
* 속도 (Speed)
* 분석복잡성(Analytic Complexity)
* 정확성&밀집도(일관성) (Accuracy&Precision)
  * ![](https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F272D643F573A1F2C1E)

## 분석 프로젝트의 특성

* 분석가의 목표 : 개별적인 분석업무 수행 뿐만 아니라 **전반적인 프로젝트 관리** 또한 중요

* 분석가의 입장

  * 데이터 영역, 비즈니스 영역의 현황을 이해
  * 분석의 정확도 달성
  * **결과에 대한 가치 이해를 팀에 전달하는 조정자로서의 역할 중요**

