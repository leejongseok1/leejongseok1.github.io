---
published: true
title: "[Tableau] 신병훈련소 DAY 4"

categories: Tableau
tag: [tableau]

toc: true
toc_sticky: true

sidebar:
    nav: "docs"
    nav: "counts"

date: 2024-01-24
---
Tableau 신병훈련소 22기 DAY 4

----

# ✏️ 학습 - 테이블 계산식

테이블 계산식을 작성하기 위해서는 무조건 **집계값**을 이용해야한다.

Tableau에서는 행 데이터를 가지고 화면에 포함된 차원을 따라 집계한 후에 그 집계된 값을 가지고 분석을 하게 된다.

분석 요건에 따라 집계값을 이용해 다시 한 번 값을 재계산해야할 경우에 테이블 계산식을 이용한다.

<br>

## 예제 1

![image](https://github.com/leejongseok1/algorithm/assets/79849878/bf02c4ba-2443-41cb-bdf9-906d85d55493)

4개년 평균 매출액과 해당연도 평균 매출액을 확인할 수 있지만 평균라인은 시각화하여 그 값을 표현해줄뿐, 실제 값 자체를 다시 계산을 하는데에 사용할 수는 없다.

집계된 합계 매출값을 가지고 다시 평균을 계산해야하는 경우에 테이블 계산식을 사용할 수 있다.

계산된 필드 만들기를 이용하여 4개년 평균 매출, 해당 연도 평균 매출 필드를 만든다.

![image](https://github.com/leejongseok1/algorithm/assets/79849878/9afbcd5e-08a5-425e-a66d-510bab3afdcd)

해당 연도 평균 매출은 연도 마다 계산이 되도록 패널을 기준으로 편집해준다.

![image](https://github.com/leejongseok1/algorithm/assets/79849878/207b7498-f987-4083-9edc-7be977fc0bad)

그 후에 매출 합계에서 4개년 평균 매출과 해당 연도 평균 매출을 빼주면 `SUM([매출]) - [4개년 평균 매출]` `SUM([매출]) - [해당 연도 평균 매출]` 4개년 평균 매출과 분기별 평균 매출을 볼 수 있다.

![image](https://github.com/leejongseok1/algorithm/assets/79849878/9f99a43c-cde9-4e22-9973-064cf295a860)

<br>

이렇게 테이블 계산식은 집계값을 기반으로 범위와 방향에 따라
- 합계
- 누계
- 순위
- 구성 비율
- 선/후행 비교
- ...

와 같은 값들을 다시 도출해낼 수 있다.

<br>
<br>
<br>

## 예제 2

아래 시각화는 연도의 월별 합계 매출액을 나타내고 있다.

전월대비 합계 매출값의 차이를 구하고자 한다.

![image](https://github.com/leejongseok1/algorithm/assets/79849878/633b43f3-f934-45df-af2c-b50be2f111ef)

<br>

행 선반에 있는 `합계(매출)`을 행에 복제하고 복제한 행의 테이블 계산을 '차이'로 바꿔주면 된다.

이 때, 계산은 예제 1에서 했던 것과 같이 연도별로 계산을 할 수 있게 '패널(옆으로)'로 설정해주고 기준을 '이전'으로 해주면 된다.

그럼 연도별 전월대비 매출 차이를 시각화할 수 있다.

![image](https://github.com/leejongseok1/algorithm/assets/79849878/f32c9f7a-ce26-4608-b3dc-18d35f66d1e8)

<br>

**테이블 계산식에서는 계산이 되는 범위를 어떻게 하느냐, 기준을 어떻게 잡느냐에 따라 다른 결과를 불러온다.**

<br>
<br>
<br>

# 📝 과제

<br>

## 1. 라인 차트 - 월별 미세먼지

![image](https://github.com/leejongseok1/algorithm/assets/79849878/7df80a15-a744-4807-9b42-942c45efc458)



<br>
<br>

## 2. 하이라이트 테이블 - 시도별 미세먼지

![image](https://github.com/leejongseok1/algorithm/assets/79849878/3398f551-573a-445f-b3fd-c86444295486)



<br>
<br>

## 3. 테이블 계산식을 이용한 시간 분석 - 국가별 빅맥 가격 변동 비율


<br>
<br>

## 4. 덤벨차트 - 빅맥 연도별 최소/최대 가격 차이

![3  덤벨차트 - 빅맥 연도별 최소 최대 가격](https://github.com/leejongseok1/algorithm/assets/79849878/409a2f19-a6e2-452e-806d-720da8e678e0)