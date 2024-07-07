# 🏰 data_modelling(데이터 모델링) 

### 📋 목차
> ### 📌 01. 데이터 모델링 이론 : 데이터 모델링의 기초 개념 
> ### 📌 02. 개념 모델링 : 계략적인 틀을 구성해 놓는 단계, 즉 설계 단계  
> ### 📌 03. 논리 모델링 : 구체적인 내용을 채워나감, 즉 설계 단계
> ### 📌 04. 물리 모델링 : 실질적으로 DB에 구현하는 단계 
> ### 📌 05. 모델링 이야기 :

<br>
<br>

## 📌 01. 데이터 모델링 이론 : 데이터 모델링의 기초 개념 
> ### 01 데이터 모델링이란? : 내가 쓸 데이터의 구조를 잡아가는 과정
> ### 02 ER 모델 구성 요소 : 엔티티, 관계, 속성, 식별자
> ### 03 관계형 데이터 모델 이론 : 릴레이션 구성, 키, 제약 조건, 함수 종속, 정규화

<br>
<br>

### 01. 데이터 모델링이란? : 내가 쓸 데이터의 구조를 잡아가는 과정 

<br>

> ### 👉 데이터 구조를 어떻게 해야 내가 읽고 쓰기 편할까에 대한 고민

- 데이터 모델링 : 데이터 구조 모델을 만드는 것 
  - 데이터 구조를 어떻게 해야 내가 읽고 쓰기 편할까에 대한 고민 
  - RDB : 관계형 DB 
    - 그룹핑 : 관련도 높은 것들끼리 묶기
    - 관계 : 서로 관계 맺기 

- ER : 엔티티와 관계로 이루어져 있음, 이를 그림으로 표현한 것이 ERD

<br>

> ### 👉 bottom-up 데이터 모델링 : 벤츠마킹 -> 하나의 엔티티 -> 분리 및 상세화 -> 관계 맺기 

- [카페 영수증]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/ccf2ee5b-ec49-4d0a-9272-b57dbafe187c" width="500" height="500"/>

- [그룹핑 결과]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/095f82b0-b010-4c6f-b464-f506ee2bd568" width="500" height="500"/>

- bottom-up 방식으로 접근, 일단 보여줘야 할 속성들 다 기록
- 해당 속성들을 포함하는 하나의 엔티티 만듦
- 이 엔티티를 관련도에 따라 분리하고 상세화함
  - 정규화 : 데이터 중복을 제거하기 위해 쪼개는 작업 
- 각 엔티티 간의 관계를 맺어줌 


<br>
<br>

### 02. ER 모델 구성 요소 : 엔티티, 관계, 속성, 식별자

> ### 👉 엔티티(개체), 관계, 속성(iv), 식별자(pk)로 이루어짐 
- 엔티티 : '실체'이거나 '개념적인' 것. 자세히 말하면, 업무를 구현하는 데 필요하고 관리해야 하는 주체, 대상, 행위 등의 모든 집합적인 것 
- [서브타입 슈퍼타입]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/5eb0a5c7-c0e1-46df-9a70-b3b3ce9814b9" width="500" height="500"/>

- [상위 수준과 하위 수준 엔티티의 일반화]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/e34ccb5b-4702-4f8c-810f-9f9a0affc906" width="500" height="500"/>

- [고객 일반화]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/b2d503d7-3f83-436d-b41f-69b920edc946" width="500" height="500"/>

- [관계]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/70cdc6fa-0f5c-4093-993f-91f5fba43af4" width="500" height="500"/>


- 관계는 크게 3가지로 구분
  - (1) 관계수 : 둘 엔티티 간의 대응되는 수를 의미, 1-1, 1-M, M-N
  - [관계수]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/ab14bcbb-cc87-4300-aafa-d2d2301183ee" width="500" height="500"/>

  - (2) 선택성 : 필수인지, 선택인지
  - [선택성]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/1eff9c4a-bea4-497b-a1f7-e36583139076" width="500" height="500"/>

  - (3) 식별성(식별자 상속) : pk이면서 fk
  - [식병성]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/af665137-47ba-4e17-8c87-c376a39a7f29" width="500" height="500"/>

- 식별성에서 잘못된 설계를 하면, 예를들어 식별자 상속 관계인데 잘못 설계하면 불피요한 인덱스를 하나 더 사용하게된다.
- 인덱스 개수가 늘어날 때 마다 성능은 급격하게 저하


- [관계 유형]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/cd4b9524-18a1-4a86-8b2c-1052757e4ef6" width="500" height="500"/>

<br>

> ### 👉 교차 테이블은 M:N관계와 병렬관계 해소하기 위해 사용됨

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/cc0e7e90-094f-456c-910a-46eafe5600ca" width="500" height="500"/>

<br>


> ### 👉 속성은 iv -> 엔티티 상태 나타냄 
- 속성명 : iv 이름
- 식별자여부 : pk인지 아닌지, 해당 속성이 엔티티 식별자에 해당하는지 표시
- 옵셔널리티 : NOT NULL 인지 아닌지 -> Mandatory, Optional, Conditional 
- 도메인 : 컬럼이 가질 수 있는 타입과 범위

<br>


> ### 👉 속성 값의 구성이나 성격에 따른 분류 -> (1)단순 속성 / 복합 속성, (2)저장 속성 / 파생 속성, (3)단일 값 속성 / 다중 값 속성 

- (1) 단순 속성 / 복합 속성 : 기본값 / 참조값(n개)
  - [단순 속성 / 복합 속성]
    
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/d7cc858f-970d-4da8-8cbb-cef3eba37d71" width="500" height="500"/>

- (2) 저장 속성 / 파생 속성 : 저장된 값 / 계산된 값
  - [저장 속성 / 파생 속성]
    
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/f531ecfe-aa28-4a26-8af8-b931e83b418b" width="500" height="500"/>

- (3) 단일 값 속성 / 다중 값 속성 : 1개 / n개 
  - [단일 값 속성 / 다중 값 속성]
    
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/63873867-1910-4b15-b2c0-535d87f3fdc1" width="500" height="500"/>
    
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/0203dd76-bbe5-4906-9028-59746b0be5cc" width="500" height="500"/>

<br>

> ### 👉 식별자의 특징 -> '유일성', '최소성', '불변성', '존재성'
- 식별자란? 엔티티에서 인스턴스를 개별적으로 식별할 수 있느 속성
- 식별자의 특징 
  - 유일성 : 엔티티의 모든 인스턴스를 유일하게 식별할 수 있어야함
  - 최소성 : 유일성을 만족하는 최소 속성들로 구성
  - 불변성 : 변하면 안됨
    - 다른 테이블의 FK로서 사용될 수 있기 때문
  - 존재성 : 값이 존재해야함 

- 식별자 유형
  - 본질 식별자 / 인조 식별자
  - 주 식별자 / 보조 식별자

- [식별자를 최소 속성으로 구성 x]
  
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/d8b50d73-cf02-4ed3-b930-13733ab12ae7" width="500" height="500"/>

- [식별자의 속성 값이 변경됨]
  
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/3b786028-07a4-4bce-9e5a-5ce27fdb697d" width="500" height="500"/>

- [본질 식별자와 인조 식별자]
  
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/45145603-492a-41f1-a135-1dabc2630bf3" width="500" height="500"/> 

  - 주문일련번호 -> 할인 이벤트가 생기면 같은 상품의 가격이 상이 할 때 문제 없이 저장할 수 있음
  - 상품코드로 사용하는 경우, 중복된 pk 발생으로 저장할 수 없음 


<br>
<br>

### 03. 관계형 데이터 모델 이론 : 릴레이션 구성, 키, 제약 조건, 함수 종속, 정규화

<br>

> ### 👉 관계형 데이터 모델(릴레이션), 관계형 모델의 키, 제약조건, 함수 종속, 정규화

- [관계형 데이터 모델]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/977b32fb-8214-4b97-b216-ce4a7a80b030" width="500" height="500"/>

- [관계형 모델의 키]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/fc8c0f34-d735-4a31-8bf5-d32662004309" width="500" height="500"/>

  - 슈퍼키 : 튜플을 고유하게 식별 할 수 있는 속성 집합
  - 후보키 : 튜플을 고유하게 식별 할 수 있는 최소한의 속성 집합
  - 기본키 : PK(NN + UQ), 유일성 + 최소성 
  - 대체키 : 기본키가 아닌 후보키 
  - 외래키 : 어떤 릴레이션의 어트리뷰트 값이 다른 릴레이션에 속한 어트리뷰트의 기본 키를 참조하는 경우


- 제약 조건
  - 키 제약조건 : UNIQUE
  - 실체 무결성 : NOT NULL
  - 영역 무결성 : 도메인에 속한 값 
  - 참조 무결성 : 참조 FK

- 함수 종속
  - [함수 종속]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/08a7b981-c692-4f6d-a4cd-4012697cffc3" width="500" height="500"/>
  
  - 수학의 집합론 기반 


- 정규화 
  - 정규화 : 중복 제거하기 위해 테이블을 쪼개는 것 
    - 데이터를 입력, 수정, 삭제할 때 발생하는 이상 현상을 최소화하기 위해 좀 더 작은 단위의 테이블로 설계 
  - (1) 이상현상 최소화
  - (2) 유연성 증가
  - (3) 재활용 높음
  - (4) 데이터 품질 문제 감소, 저장공관 최소화
  - (5) 데이터 입력, 수정, 삭제시 작업을 최소화 
  - 정규화를 너무 많이 할 경우 다시 역정규화 할 수 있음
  
- 제 1 정규화 : 컬럼 원자성
  - [제 1 정규화]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/903a33ee-1e7c-43e5-94cc-93683dcdf9bc" width="500" height="500"/>
  - 컬럼 원자성, 관계형 테이블은 중복되는 행이 없어야 하고, 모든 열의 값은 원자값을 가져야함 
    

- 제 2 정규화 : 부분 종속 해소
  - [제 2 정규화]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/d8fceca8-1483-418f-aa5e-a5bacf3a12ba" width="500" height="500"/>
  - 후보키에 종속적이지 않거나 후보키 일부 어트리뷰트에 종속적인 어트리뷰트는 별도 릴레이션으로 분리해야함 

- 제 3 정규화 : 이행적 종속 해소
  - [제 3 정규화]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/280c9bd4-2895-4d3f-ad1c-7fd8a4b8154b" width="500" height="500"/>
  - 키가 아닌 어떤 어트리뷰트가 다른 어트리뷰트에 종속된 경우 별도 릴레이션으로 분리 

  
<br>
<br>

## 📌 02. 개념 모델링 : 계략적인 틀을 구성해 놓는 단계, 즉 분석 단계  
> ### 01 데이터 모델링 접근 방법 : 데이터 모델링 작업 흐름 
> ### 02 개념 모델링 : 개략적인 데이터 모델을 구성

<br>

### 01 데이터 모델링 접근 방법 : 데이터 모델링 작업 흐름 

> ### 👉 데이터 모델링 절차 : '분석 & 요구사항 -> 계획 수립 -> 설계 -> 구현' 
- [데이터 모델링 절차]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/cf1f307d-70c6-4b58-81e4-9ac0849f4520" width="500" height="500"/>

- 위의 과정을 좀 더 쉽게 4단계로 구분하면 다음과 같음 
  - (1) 주제 선정 : 주제 및 벤치마킹 사이트 선정 
  - (2) 핵심 엔티티 도출 : 주제 영역에서 나타나는 사건을 분석 -> 핵심 키워드 도출
  - (3) 파생 엔티티 & 관계 맺기 : 파생 엔티티(상태/상세/이력/교차), 관계(관계수/존재성/식별자상속)
  - (4) 속성 정의 : 도메인, 조건 ... 수립
- top-down/ bottom-up 2가지 방식이 있음

- 현행 분석 및 방향성 수립 : ERD, 테이블 정의서, 사용자 메뉴얼 .. 산출물 최대한 수집 & 인터뷰 
- AS-IS : 현행 분석 & 요구 사항 정의 => TO-BE : 개선 방향
- 사실, 실무에서는 산출물 수집이 어려움 -> 리버스 모델 활용 : 물리 -> 논리, 거꾸로 유추함



<br>


### 02 개념 모델링 : 개략적인 데이터 모델을 구성 


> ### 👉 개념 모델링 -> (1) 주제영역 도출 / (2) 주제영역 분류 및 정의 / (3) 핵심 엔티티 정의 및 관계 정의 

- 주제영역 : <strong>'업무별 데이터 종류 나누기'</strong>
  - 벤치 마킹 사이트에서 인사이트를 얻기도 함
  - [주제영역 도출]

  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/ddff6651-fe00-42e0-89d7-bb7f97fa5472" width="500" height="500"/>

- 주제영역 분류 및 정의 : <strong>각 각 계략적으로 정의</strong>
  - 주제영역 도출 -> 분류 및 그룹핑 
  - 글쓰기 적극 활용 
  - [주제영역 프레임 워크]

  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/a816697b-6ef3-419d-867a-47add8a18cb6" width="500" height="500"/>
  
  - [주제영역 분류]

  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/123f9384-6757-4b6a-9992-4bc8d61824a1" width="500" height="500"/>
  
  - 주제 영역 정의에 따라서 범위(도메인)가 달라짐
    - 예를 들어서 고객을 내국인으로 할지, 외국인으로할지, 아동포함 ... 

  - [주제영역정의서]

  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/d4403160-e59b-479c-84d1-690b12946138" width="500" height="500"/>

- 핵심 엔티티 정의 및 관계 정의 : <strong>핵심 테이블 정의</strong>
  - 데이터 주제영역별로 대표성을 갖는 핵심 엔티팉 도출하고 식별
  - 핵심 엔티티 : 주제영역과 마찬가지로 업무 주체, 대상, 자원, 장소 등에 해당하는 엔티티
    - 고객 주제 영역 -> 고객, 거래처, 신용평가, 채널
    - 업무 행위에 관련있는 핵심 엔티티 -> 계약, 주문, 입출금, 발주번호
  - 글로 쓰다보면 문장 속에서 핵심 엔티티 도출할 수 있음  

<br>
<br>

## 📌 03. 논리 모델링 : 구체적인 내용을 채워나감, 즉 설계 단계 
> ### 01 논리 모델링이란 : 데이터를 명확하고 구체적으로 정의하는 단계
> ### 02 엔티티 정의 및 상세화 : 엔티티를 명확하게 분류하는 작업 -> 핵심/중요/행위
> ### 03 관계 도출 및 정의 : 엔티티 간의 관계 맺기 -> 관계수 / 선택성 / 식별자 상속
> ### 04 속성 도출 및 정의 : 최대한 모든 속성 도출하고 정의
> ### 05 데이터 표준화 : 일관성을 유지함 -> 의사소통 원할히/ 개발 생산성 증대 


<br>
<br>

### 01 논리 모델링이란 : "데이터를 명확하고 구체적으로 정의하는 단계"

> ### 👉 데이터를 구체화 -> 상세한 수준의 데이터 구조 설계 

- 개념 모델링과 논리 모델링을 번갈아 가면서 진행하여 발전시킴 -> 구조적 일관성을 유지 
- 이 단계에서는 DBMS의 물리적 특성까지 고려하지 않음 



<br>

### 02 엔티티 정의 및 상세화 : 엔티티를 명확하게 분류하는 작업 -> 핵심/중요/행위

> ### 👉 도출된 핵심 엔티티에서 더욱 세분화하여 핵심/중요/행위 엔티티를 정의하고 분류하는 작업

- ### 핵심 엔티티 : 독립적으로 존재, 업무에 미리 정의된 엔티티 -> '명사'
  - 고객, 부서, 직원, 상품 ... 
- 업무 행위의 주체가 되거나 행위의 대상이 되는 경우가 많음
- 핵심 엔티티는 크게 4가지로 구분
  - (1) 유형 및 분류 : 카테고리 대/중/소 분류, 고객유형코드, 상품분류코드 -> 계층 구조를 갖음 
    - [유형 및 분류]
    - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/6da697ef-9cf3-4b54-885e-3aef0da50f5f" width="500" height="500"/>
  - (2) 업무규칙 및 지식 : 업무처리를 위한 각종 규정과 지식, 조건 -> 회원등급, 보험료 조건, 직급별 연봉
    - [서비스 - 자격, 자격 - 요건 업무규칙 정의]
    - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/4780e8c2-972a-49a7-9696-857adcb10d7d" width="500" height="500"/>
  - (3) 업무줴 및 대상 : 이벤트 주체 또는 대상 -> 부서, 사원, 고객, 상품
    - [업무 주체 및 대상]
    - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/e6ebe7fd-6435-4233-93a5-4485bc3736cd" width="500" height="500"/>
  - (4) 장소 : 이벤트가 발생하는 곳 -> 공장, 도로, 채널 
    - [장소]
    - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/210b447d-bf9c-40ce-813c-fb6a554a82a3" width="500" height="500"/>

<br>

- ### 중요 엔티티 : 업무 행위 자체를 나타내는 엔티티 -> '동사' 
  - 주문, 약정, 입출고
- 업무 행위의 주체나 대상에 종속되는 경우가 많음 
- 업무의 핵심 기능과 밀접한 관련, 주요 업무에서 반복하여 발생하는 데이터를 관리 
  - [업무영역 중요 엔티티]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/1bccbc0e-d4af-472b-aedf-b644f0f563d1" width="500" height="500"/>
  - [계좌는 고객과 상품 간의 관계 엔티티]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/86acda6e-c828-4bc9-a5c1-0b85aa6709d7" width="500" height="500"/>
  
  
<br>

- ### 행위(파생) 엔티티 : 업무 행위로부터 발생하는 데이터를 나타내는 엔티티 -> '결과'
  - 주문내역, 결제내역, 배송지상세내역 
- 업무 행위에 따른 결과를 상태로 나타내는 엔티티
- 중요 엔티티에 종속되거나 다른 행위 엔티티에 종속되는 경우가 많음 
  - [행위 엔티티 유형]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/3469ef5a-be5f-44bf-a619-08e841d00252" width="500" height="500"/>
- 크게 4가지로 구분할 수 있음 
  - (1) 상세/내역 : 중요 엔티티에 해당하는 행위 엔티티를 구성하는 항목 단위로 분류
    - 품의내역, 입찰품목내역, 예산내역
  - (2) 상태 : 업무는 단계적으로 처리됨, 또한 업무를 처리하는 흐름이 있음 
    - [결재 프로세스]
    - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/250789a8-f4d3-4b6e-a33e-045fdebfa55a" width="500" height="500"/>
  - (3) 이력 : 데이터가 변경되었을 때 변경 전 데이터를 추가로 관리 
    - 이력의 경우 어느 범위까지 관리할지, 현재를 포함할지 말지, 점으로 관리할지 선분으로 관리할지에 따라 여러 형태로 나뉨
    - 이력관리는 크게 5가지로 구분
      - (1) 점 이력 : 변경 시점을 이벤트로 관리
      - (2) 선분 이력 : 변경 시점을 구간으로 관리 
      - (3) 전체 이력 : 전체 항목 관리 
      - (4) 일부 이력 : 변경 항목만 관리
      - (5) 현재값 포함 : 현재 값도 포함해서 관리 
        - [이력 엔티티]
        - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/b37b28c7-ab71-4937-94a5-5d5247493b14" width="500" height="500"/>
        - [이력관리 범위 및 형태]
        - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/eeacbfc4-f1d2-4e97-bde7-b429c5b94fe0" width="500" height="500"/>
        - [변경 항목만 이력 관리]
        - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/27671a21-a9cb-4abf-a60a-2a032323e746" width="500" height="500"/>
        - [점 이력]
        - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/fb1178b6-3835-4b5f-9927-28d1371a0748" width="500" height="500"/>
        - [선분 이력]
        - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/f359ef7e-ec1c-4107-b84e-8f51b2ba5d74" width="500" height="500"/>
        - [최종 데이터 포함 이력]
        - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/6acd4d2a-8188-4186-b4ce-23e9638cd8dc" width="500" height="500"/>
        - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/a69e8291-7bc1-45a7-b6a0-adf83aa98d5c" width="500" height="500"/>  
  - (4) 기타(교차) : 교차 테이블 활용 위에 '교차 테이블' 참고

<br>

> ### 👉 논리 모델링 단계에서는 모든 것이 명확하고 상세해야함 
- 단어 및 용어 통일, 구체적인 용어 사용
  - [앤티티명 명명 규칙 예시]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/ae99299d-5f6c-45e1-9d3b-20c67ce0e05f" width="500" height="500"/> 

<br>
<br>

### 03 관계 도출 및 정의 : 엔티티 간의 관계 맺기 -> 관계수 / 선택성 / 식별자 상속


> ### 👉 주체나 대상에 해당하는 속성 등을 파악해서 관계를 도출 -> 주체 / 대상 / 상세 / 인과 / 역할&자격 / 구성&포함 / 참조
  - [관계 도출 대표 예시]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/236350e9-6d11-4d59-a5ba-1c6eb15a6ae6" width="500" height="500"/>
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/f25132a1-56af-431f-a270-adf9a634af36" width="500" height="500"/> 
<br>

> ### 👉 관계를 맺을 때는 양방향으로 맺는다.
- [관계 정의]

- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/27c9ff38-98c0-4bd4-a795-cdf5ff92d78c" width="500" height="500"/>
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/dce799c4-4b2c-46fb-833b-5bdb991eb157" width="500" height="500"/>
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/380966b8-fb7a-4a67-9311-6fc4bdfdb2bb" width="500" height="500"/>
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/5e46b5a9-8d15-4b4b-927f-b2ff0cb1837d" width="500" height="500"/>
  
- (1) 선택수 : A가 있다면 B는 최대 몇 개까지 가능할까? B가 있다면 A는 최대 몇 개까지 가능할까?
- (2) 선택성 : A가 있다면 B는 있어야 할까? B가 있다면 A는 있어야 할까?
- (3) 식별자 상속 : A와 B는 긴밀한 관계인가?


<br>

### 04 속성 도출 및 정의 : 최대한 모든 속성 도출하고 정의 

> ### 👉 컬럼(iv)를 생각 나는대로 적기(브레이닝스토밍), 여유분 확보 추후에 컬럼 추가하기 매우 어려움

- 모든 속성을 도출하는 것이 중요 -> 화면에서 보여줄 것, 시스템 내부적으로 필요한 것 까지 파악
- 컬럼에 대한 설명이 명확해야함 
- 업무에 필요한 데이터를 다 넣을 수 있어야함 
- [속성 종류]
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/5020d0ed-71b7-46e9-8f12-6ed6d43a6f70" width="500" height="500"/>
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/f0c973ef-3513-4b9f-b0cc-dce90aae4698" width="500" height="500"/>

<br>

> ### 👉 속성명 부여 및 정의는 명확하게 
- 속성명 : 속성을 명확하게 설명할 수 있는 명칭 부여
- 속성 정의 : 속성에 대한 설명이나 데이터 발생 규칙 등을 기술
  - 어떤 데이터가 언제 저장되는지 


<br>

> ### 👉 식별자는 "유일성, 최소성, 불변성, 존재성"을 만족하는 컬럼으로 지정
- 식별자는 크게 2가지로 구분
  - (1) 본질 식별자 : 원래 존재하는 속성
  - (2) 인조 식별자 : 인위적으로 부여한 일련번호 

<br>

- 인조 식별자를 사용하는 경우는 4가지
  - (1) 엔티티를 통합하는 경우 : '엔티티를 통합할 때 통합 대상 엔티티 식별자가 서로 다르거나, 데이터 집합 단위가 다른 경우'
  - [복잡한 본질 식별자 대체]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/a7a661dc-2dc0-48c7-bcb0-5fdf715c76ea" width="500" height="500"/>

<br>

  - (2) 키가 너무 많은 경우 : '업무적으로 중요성은 덜하지만 본질 식별자인 발주번호 + 입찰마감일자 대신 인조 식별자 사용'
  - [복잡한 본질 식별자 상속 대체 ]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/8403c8cc-ee21-4184-a55e-6eb635c2a1f9" width="500" height="500"/>

<br>

  - (3) 암호화 해야하는 경우 : '개인정보 암호화 대상에 해당하여 본질 식별자를 주 식별자로 사용하는 경우'
  - [암호화 식별자 대체]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/a3e37f18-5f11-4659-b11f-aeaf79b475cc" width="500" height="500"/>  

<br>

  - (4) 업무적으로 나중에 처리해야 하는 경우 : '본질 식별자에 대한 데이터가 들어오지 않은 상태에서 업무 처리를 위해 사용'
  - [초기 Null 값이 있는 본질 식별자 대체]
  - <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/3e332fb7-ae5d-475f-af7e-3c0e90542f13" width="500" height="500"/>


<br>

> ### 👉 데이터 모델 검토, 자체 검토하거나 팀끼리 검토 하는 방법이 있음 

- [데이터 모델 체크리스트]
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/c2f2ba04-c3c3-4679-a685-2f5ec013903d" width="500" height="500"/>

<br>
<br>

### 05 데이터 표준화 : 일관성을 유지함 -> 의사소통 원할히/ 개발 생산성 증대 

<br>

> ### 👉 일정부분 형식화 된 것들 활용하거나 팀원끼리 정의해야함 
- [표준구성요소]
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/ad5bfba3-a37f-4d73-bee1-dba154d77ef1" width="500" height="500"/>
- 표준단어 : 의미를 가지는 최소 단위의 낱말
- 표준도메인 : 단어 또는 용어의 일종, 데이터 값의 형식과 범위를 포함
- 표준코드 : 도메인의 일부, 도메인이 코드 성격을 가지는 경우 허용되는 값의 범위를 특정 값들로 한정하고 목록화된 데이터 값만 사용할 수 있도록함 
- 표준용어 : 현업이 엄무에서 사용하는 업무 용어 
- 저자가 정리한 단어사전 -> https://blog.naver.com/easttree/221850248981?viewType=pc

<br>

> ### 👉 도메인 표준화 -> 데이터에 대한 형식과 범위를 규정 / 코드 표준화 -> 업무에서 통계를 내거나 한정된 데이터 값을 목록화하여 관리하고자 하는 대상을 코드로 식별하여 정의  
- [도메인 사전]
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/16e7acdd-40b9-4930-859a-f8a955008796" width="500" height="500"/>
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/2a3efdcb-8969-4160-8706-05c98ccae986" width="500" height="500"/>

<br>

- [코드 사전]
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/d32eace2-0d9b-49e9-bdf7-8d8d14a59305" width="500" height="500"/>

<br>

- [코드 수식어]
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/0f460cbf-c437-467b-8ce1-fed3bcfc4d8d" width="500" height="500"/>

<br>

- [코드 부여]
- <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/385b6a44-24a0-42a2-b430-db98f9f45db0" width="500" height="500"/>

<br>
<br>

## 📌 04. 물리 모델링 : 실질적으로 DB에 구현하는 단계 
> ### 1. 믈리 모델링이란 : 논리 모델링 실제 구현
> ### 2. 테이블 설계
> ### 3. 관계 설계
> ### 4. 컬럼 설계
> ### 5. 데이터 무결성 설계 
> ### 6. 성능을 고려한 데이터 구조 


### 1. 믈리 모델링이란 : 논리 모델링 실제 구현

> ### 👉 논리 모델링을 구현하는 단계
- 엔티티 -> 테이블, 속성 -> 컬럼, 관계 및 무결성 설계, 반정규화, 중복 컬럼 추가 

<br>

### 2. 테이블 설계 : 

> ### 👉
