---
published: true
title: "[Tableau] 신병훈련소 DAY 6"

categories: Tableau
tag: [tableau]

toc: true
toc_sticky: true

sidebar:
    nav: "docs"
    nav: "counts"

date: 2024-01-29
---
Tableau 신병훈련소 22기 DAY 6

----

# ✏️ 학습 - 고급계산식

## 세부 수준 계산식 (LoD: Level of Detail Expression)

{ [ INCLUDE | EXCLUDE | FIXED ] [차원] ... :집계식( [측정값] ) }

화면상의 세부 수준(LoD)와 관계 없이 계산이 필요한 경우에 사용

- 고객 당, 주문 당 등 '~당' 계산이 필요한 경우
- 집계를 다시 집계해야 하는 상황
- 집계 결과를 기준으로 구간을 나눠야 하는 경우
- 뷰에서 보고 있는 수준 보다 아래 또는 위 수준에서 계산 결과를 만들어야 하는 경우

<br>

**시각화 세부 수준의 구성 요소**

기본적으로 Tableau는 집계 값을 통해 시각화한다.

이 때, 집계의 기준은 "시각화의 세부 수준"에 따라 결정된다.

시각화에 추가되는 차원에 따라 집계의 기준이 변경되는데, 측정값의 집계 기준을 **시각화의 세부 수준** 또는 **뷰의 수준**이라고 한다.

이러한 시각화 세부 수준에 영향을 미치는 곳은 아래 그림에 빨간 박스로 표시된 곳이다.

빨간 박스에 추가되는 "**차원**"이 시각화의 세부 수준을 결정 짓는다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/2a0da7de-a951-4dea-a7b8-85e9ddaec830)

<br>

아래 사진 처럼 제품 중분류가 뷰에 추가되어있지만 제품 대분류별 매출액을 보고 싶을 때,

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/dad18a61-c720-4e4b-a21e-60624dcfe3c1)

제품 대분류를 수준으로 전체 매출액을 집계하는 계산식을 만들면 된다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/45d79171-de38-4ea0-8c29-45f567be3a27)

그럼 Fixed의 값들은 제품 중분류가 빠질 때의 전체 합계값과 동일하다.

각각의 중분류의 제품 대분류 수준으로 집계된 값이 중복해서 보여지게 된다.

제품 대분류로 FIXED 하겠다는 뜻은 중분류 차원을 고려하지 않겠다라는 뜻인데,

EXCLUDE를 사용해 중분류를 제외시켜도 동일한 값이 나온다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/b4c09790-fd4a-4181-8e31-9c65d3d979bf)

> INCLUDE는 뷰 세부수준에 포함되지 않는 차원이지만 계산식에는 고려하여 집계를 하고싶을 때 사용한다.

<br>
<br>

### 유입 시점별 고객 매출 기여도: 2014년도에 처음 구매한 고객이 2017년도 매출에 얼마나 기여하고 있을까?

MIN([주문일자])는 전체 고객의 첫 구매시점을 반환한다.

이 때 FIXED를 써서 고객당 첫 구매시점을 반환하도록 한다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/1bd3c0c0-1252-40c0-af79-14d671b71b06)


![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/2a673946-bc85-467b-a33a-df852850cb88)

<br>
<br>

### 주문번호 당 평균 매출 금액

매출의 측정값을 단순히 '평균'으로 바꾼다면,

주문번호 당 평균 매출 금액이 아니라 전체 합계를 레코드 수로 나누게 될 것이다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/c33e8d6d-13b4-498e-a219-554d3460e171)

<br>

하지만 우리가 궁금한 것은 주문번호 당 평균 매출 금액이다.

단순하게 분석 탭에서 평균 라인을 그려보면 평균 수치를 알 수도 있다.

하지만 주문번호는 궁금하지 않고 주문번호 당 평균 매출 금액만 수치로 표현하고 싶다면, (뷰에 없는 차원으로 계산해야할 때)

LoD 계산식을 사용해야한다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/2ce01f87-f6fe-480c-acbd-69cd4bbe22c0)

<br>

**[분석] - [평균라인]**

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/240e5f3d-dc5f-4b5c-ba49-32da91b09a59)

<br>

**LoD 계산식 사용 - INCLUDE**

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/1ab5c078-2e07-4157-908e-f8417df0cad2)

<br>

**LoD 계산식 사용 - FIXED**

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/c94ca9d5-bf57-4099-a1e9-23703c56d16b)

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/c2bfd867-089f-4539-a2c5-5506f2cac80c)

> Tableau LoD Expression 을 검색하면 LoD를 사용하여 분석할 수 있는 예시가 나와있다고하니 참고하자.

<br>
<br>

## 테이블 계산

테이블 계산 | 기존 집계 계산의 결과 집합 위에 추가 계산을 실행

<br>

**테이블 계산식의 원리**

"Raw Data"를 "집계한 값 (Aggregation)"을 가지고 "테이블 계산 (Table Calculation)"을 실행한다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/50062995-abbb-4e25-9377-c00dd755f839)


----

측정값은 시각화의 세부 수준에 따라 집계가 되고, 이 집계 값을 갖고 다시 재계산 해야 하는 테이블 계산은 어떤 기준으로 계산을 해야할 지 지정해줘야 한다. 이 때, 재계사닝 되는 범위(테이블, 패널, 셀)와 방향, 기준에 따라 값이 달라질 수 있기 때문에 범위와 방향을 신중하게 설정해줘야 한다.

<br>
<br>

### 정렬: 지역별 Top 3 (매출 기준) 제품 찾기

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/c7c5b44d-21e3-452b-8487-019710ba047e)

강의 영상을 보니 지역과 제품 중분류 둘다 정렬을 했을 때

의자보다 책장의 매출이 높음에도 의자가 더 위에 있는 문제가 있었다.

이럴 때 사용하는 테이블 계산인 것 같은데 강의 영상이 6년 전이다 보니..

그 사이 Tableau에서 업데이트 한 것 같다.

그래도 테이블 계산이 무엇인지 알아는 보자!

매출 합계를 세부정보에 놓은 뒤 [퀵 테이블 계산] - [순위] 를 누르고

지역마다 순위가 계산될 수 있도록 패널(아래로) 계산을 한다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/12dc3621-ce3a-41f8-93fb-e85eb41c216e)

테이블 계산 한 매출 합계 필드는 불연속형으로 바꿔주고

1 ~ 3위를 필터 걸어주면

다음과 같이 지역별 매출액 순위를 볼 수 있다!

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/5324edbe-b84a-4d48-a851-4698a6595150)

<br>
<br>

### 기록 수익: 분기 별 수익이 최대 수익일 때 확인하기

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/6c73e54f-40e1-48a0-ac0c-60ae6a59a872)


<br>
<br>
<br>

# 📝 과제

<br>

## 1. 테이블 계산식 - 차이 : 전일 대비 종가 등락

![1  전일 대비 종가 등락](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/f296daea-999e-40d7-9fce-1e7a9eab5d92)

<br>
<br>

## 2. 테이블 계산식 - 구성비율 : 전국기준 매출 구성비율

![2  전국기준 매출 구성비율](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/f8f92019-aecd-4ef1-8144-43db1bcf52d6)

<br>
<br>

## 3. 세부 수준 계산식(LoD) - 전국 기준 매출 구성비율 : 지역기준/ 전국기준 매출 구성비 함께 보기

![3  세부수준 계산식(LOD) - 전국 기준 매출 구성비율 구하기](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/65baecbc-8499-4f8a-b1c0-bd9f52c31302)

<br>
<br>

## 4. 세부 수준 계산식(LoD) : 과거 고객 매출 기여도 및 신규 유입 고객 현황 분석

![4  과거 구매 고객의 매출 기여도](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/1fb893b4-1ec2-45f4-aba7-cc6a1462d889)

<br>
<br>

## [추가 도전] 코호트 분석 : 과거 구매 고객의 매출 기여도

![5   추가도전과제  코호트 분석 - 고객당 재구매 시점까지 경과 기간](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/d8cea398-cab9-4fb8-bc15-e6407cbbb9a6)


<br>
<br>