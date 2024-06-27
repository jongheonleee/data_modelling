# data_modelling

## 01. 데이터 모델링 이론

### 01. 데이터 모델링이란?

> ### 👉 데이터 구조를 어떻게 해야 내가 읽고 쓰기 편할까에 대한 고민

- 데이터 모델링 : 데이터 구조 모델을 만드는 것 
  - 데이터 구조를 어떻게 해야 내가 읽고 쓰기 편할까에 대한 고민 
  - RDB : 관계형 DB 
    - 그룹핑 : 관련도 높은 것들끼리 묶기
    - 관계 : 서로 관계 맺기 

- ER : 엔티티와 관계로 이루어져 있음, 이를 그림으로 표현한 것이 ERD

> ### 👉 bottom-up 데이터 모델링 : 벤츠마킹 -> 하나의 엔티티 -> 분리 및 상세화 -> 관계 맺기 

- [카페 영수증]

<img src="https://github.com/jongheonleee/data_modelling/assets/87258372/ccf2ee5b-ec49-4d0a-9272-b57dbafe187c" width="500" height="500"/>

- [그룹핑 결과]

<img src="https://github.com/jongheonleee/data_modelling/assets/87258372/095f82b0-b010-4c6f-b464-f506ee2bd568" width="500" height="500"/>

- bottom-up 방식으로 접근, 일단 보여줘야 할 속성들 다 기록
- 해당 속성들을 포함하는 하나의 엔티티 만듦
- 이 엔티티를 관련도에 따라 분리하고 상세화함
  - 정규화 : 데이터 중복을 제거하기 위해 쪼개는 작업 
- 각 엔티티 간의 관계를 맺어줌 


### 02. ER 모델 구성 요소 

> ### 👉 엔티티(개체), 관계, 속성(iv), 식별자(pk)로 이루어짐 
- 엔티티 : '실체'이거나 '개념적인' 것. 자세히 말하면, 업무를 구현하는 데 필요하고 관리해야 하는 주체, 대상, 행위 등의 모든 집합적인 것 
- [서브타입 슈퍼타입]

<img src="https://github.com/jongheonleee/data_modelling/assets/87258372/5eb0a5c7-c0e1-46df-9a70-b3b3ce9814b9" width="500" height="500"/>

- [상위 수준과 하위 수준 엔티티의 일반화]

<img src="https://github.com/jongheonleee/data_modelling/assets/87258372/e34ccb5b-4702-4f8c-810f-9f9a0affc906" width="500" height="500"/>

- [고객 일반화]

<img src="https://github.com/jongheonleee/data_modelling/assets/87258372/b2d503d7-3f83-436d-b41f-69b920edc946" width="500" height="500"/>

- [관계]

<img src="https://github.com/jongheonleee/data_modelling/assets/87258372/70cdc6fa-0f5c-4093-993f-91f5fba43af4" width="500" height="500"/>


- 관계는 크게 3가지로 구분
  - (1) 관계수 : 둘 엔티티 간의 대응되는 수를 의미, 1-1, 1-M, M-N
  - [관계수]
  <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/ab14bcbb-cc87-4300-aafa-d2d2301183ee" width="500" height="500"/>

  - (2) 선택성 : 필수인지, 선택인지
  - [선택성]
  <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/1eff9c4a-bea4-497b-a1f7-e36583139076" width="500" height="500"/>

  - (3) 식별성(식별자 상속) : pk이면서 fk
  - [식병성]
  <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/af665137-47ba-4e17-8c87-c376a39a7f29" width="500" height="500"/>

- 식별성에서 잘못된 설계를 하면, 예를들어 식별자 상속 관계인데 잘못 설계하면 불피요한 인덱스를 하나 더 사용하게된다.
- 인덱스 개수가 늘어날 때 마다 성능은 급격하게 저하


- [관계 유형]

<img src="https://github.com/jongheonleee/data_modelling/assets/87258372/cd4b9524-18a1-4a86-8b2c-1052757e4ef6" width="500" height="500"/>


> ### 👉 교차 테이블은 M:N관계와 병렬관계 해소하기 위해 사용됨

<img src="https://github.com/jongheonleee/data_modelling/assets/87258372/cc0e7e90-094f-456c-910a-46eafe5600ca" width="500" height="500"/>


> ### 👉 속성은 iv -> 엔티티 상태 나타냄 
- 속성명 : iv 이름
- 식별자여부 : pk인지 아닌지, 해당 속성이 엔티티 식별자에 해당하는지 표시
- 옵셔널리티 : NOT NULL 인지 아닌지 -> Mandatory, Optional, Conditional 
- 도메인 : 컬럼이 가질 수 있는 타입과 범위


> ### 👉 속성 값의 구성이나 성격에 따른 분류 -> (1)단순 속성 / 복합 속성, (2)저장 속성 / 파생 속성, (3)단일 값 속성 / 다중 값 속성 

- (1) 단순 속성 / 복합 속성 : 기본값 / 참조값(n개)
  - [단순 속성 / 복합 속성]
    <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/d7cc858f-970d-4da8-8cbb-cef3eba37d71" width="500" height="500"/>

- (2) 저장 속성 / 파생 속성 : 저장된 값 / 계산된 값
  - [저장 속성 / 파생 속성]
    <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/f531ecfe-aa28-4a26-8af8-b931e83b418b" width="500" height="500"/>

- (3) 단일 값 속성 / 다중 값 속성 : 1개 / n개 
  - [단일 값 속성 / 다중 값 속성]
    <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/63873867-1910-4b15-b2c0-535d87f3fdc1" width="500" height="500"/>
    <img src="https://github.com/jongheonleee/data_modelling/assets/87258372/0203dd76-bbe5-4906-9028-59746b0be5cc" width="500" height="500"/>

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
  <img src="" width="500" height="500"/>

- [식별자의 속성 값이 변경됨]
  <img src="" width="500" height="500"/>

- [본질 식별자와 인조 식별자]
  <img src="" width="500" height="500"/> 
  - 주문일련번호 -> 할인 이벤트가 생기면 같은 상품의 가격이 상이 할 때 문제 없이 저장할 수 있음
  - 상품코드로 사용하는 경우, 중복된 pk 발생으로 저장할 수 없음 


### 03. 관계형 데이터 모델 이론 