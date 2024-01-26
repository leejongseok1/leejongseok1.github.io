---
published: true
title: "[Tableau] 신병훈련소 DAY 5"

categories: Tableau
tag: [tableau]

toc: true
toc_sticky: true

sidebar:
    nav: "docs"
    nav: "counts"

date: 2024-01-25
---
Tableau 신병훈련소 22기 DAY 5

----

# ✏️ 학습 - 맵

![1F](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/de360a9e-51e8-41d1-951e-d4c4f45e2022)

매장도 이미지가 얼마만큼의 크기를 갖고 있는지, 전체 X와 Y의 크기를 알 수 있다.

X와 Y를 기준으로 실제 매장들이 어디에 위치하는지 각각의 좌표값들을 불러올 수 있다.

열과 행에 (X, Y)를 나타내고 그 마크에 대해 매출의 합계를 크기와 색상으로 표현하면 다음과 같은 시각화를 나타낼 수 있다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/819ee103-7b1a-4af1-8abd-00465954b227)

<br>

## 실습 1 - 배경이미지 맵

X와 Y를 각각 열과 행 선반에 놓고 층별, 층에서 각 매장수준까지 나타내면 무언가가 표현이 되는 것처럼 나타난다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/deffdb14-00b3-419f-a244-444531ce0084)

<br>

상단바 **맵**에서 **배경이미지**를 클릭하고 어떤 데이터에 접목을 시킬지 선택한다. (사용하고 있는 데이터)

이미지 추가를 선택해 사용하고자 하는 이미지를 가져온다. 

X에는 전체 이미지의 가로길이, Y에는 전체 이미지의 세로길이를 주어야한다.

옵션 - 다음 경우에만 표시에서 `Floor(매장 좌표)`가 `1F`일 때만 표현하도록 한다. (`2F`도 같은 방법으로 진행)

그럼 아래 사진과 같이 매장도를 나타낼 수 있다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/e27e798d-8b3e-4355-b55d-9f807fa0f313)

<br>

그 다음, 매출 합계를 크기와 원하는 색상으로 표현하면 각각의 매장별 매출을 한 눈에 비교하기 쉬운 시각화를 그릴 수 있다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/f9aafed7-ece4-4ac1-bed7-901f346f3146)

<br>
<br>

## 실습 2 - 공간 계산식

각각의 카페별 위경도값을 가지고 있는 데이터로 시각화를 표현해보려고 한다.

데이터의 위도와 경도를 행과 열 선반에 가져다놓고, 맵을 `거리`로 나타내면 다음과 같은 화면이 나타난다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/6b6c0aff-29ac-4af9-9941-90c5a6f2ea85)

이제 공간계산식을 사용해 실제 카페별로 얼마만큼 영업권이 겹치는지 표현해볼 것이다.

Buffer 함수와 MAKEPOINT 함수를 이용하여 계산된 필드를 만든다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/1f308437-e692-4413-8dd9-156f1e5a36aa)

만든 계산식을 세부정보에 추가해주면 카페별로 100m 이내에 얼마만큼 영업권이 겹치는지 볼 수 있다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/4ee85d4c-f0e4-4823-b1f8-a5058d17cc9c)

<br>
<br>
<br>

# 📝 과제

## 1.  배경 이미지를 이용한 Custom Map 사용하기 

**사용 Data - 2호선 역별 승하차인원수**

![1-1  일별 평균 승하차 승객수 - 계산식](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/61de7d92-ba63-45c9-a94c-0ae27f1f3ff0)

![1  일별 평균 승하차 승객수](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/6f12e10a-d7b2-4ca6-87ad-7def03a5f0d9)

<br>

## 2. 공간 테이블 계산을 이용한 맵 활용

**사용 Data - Airports Extract**

**시애틀에서 출발한 항공편의 취향지별 승객 수**

<br>

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/1621260f-8c67-4a3a-bd82-2a1109002063)

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/4519bd73-9ab8-4029-b3b0-a0fee020fd94)

<br>

**비행경로 라인 그리기**

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/54764c28-6253-4c75-8953-52ce58afb8e9)


![2  공간 테이블 계산을 이용한 맵 활용](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/fd7c1648-6d4c-400a-81c9-3fb3f18f2a91)

<br>
<br>

## 3. Buffer 함수를 이용한 맵 활용

**사용 Data - 전국 주유소 추출**

**내가 선택한 반경 안에 동종 업계가 얼마나 포진해 있는지**

**주유소 위치와 각 위치 별로 선택한 반경 시각화**

<br>
<br>

매개변수 만들기

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/d7da6a45-9db9-414d-b15f-d1f5116ae432)

<br>

만든 매개변수를 이용해 계산식 만들기

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/3c01da64-124d-4c66-8a68-9ee17d44a606)

<br>

상단 메뉴 > 맵 > 배경 맵 > 거리 선택

상단 메뉴 > 맵 > 백그라운드 레이어 선택

마크에 필드를 알맞게 가져다놓기

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/ebf324cb-2632-47ce-80af-cfd0f23b479c)