---
published: true
title: "[Tableau] 신병훈련소 DAY 8"

categories: Tableau
tag: [tableau]

toc: true
toc_sticky: true

sidebar:
    nav: "docs"
    nav: "counts"

date: 2024-02-01
---
Tableau 신병훈련소 22기 DAY 8

----

# ✏️ 학습 - 집합

태블로 집합이란?

**Q)** 태블로 사용기간이 6개월 이상인가?

**A1)** YES. (태블로 사용기간 >= 6개월)

**A2)** No. (태블로 사용기간 < 6개월)

<br>

태블로의 집합은 **조건**을 기반으로 하나의 영역을 **IN**과 **OUT**으로 **분리**

> 필터 : **IN**에 속하는 멤버만 유지


<br>
<br>

## 집합을 만드는 방법 - 동적 집합 / 정적 집합

1. 분석 화면에서 직접 멤버 선택
2. 만들기 -> 집합 ... 메뉴 활용
    - 직접 멤버 선택 (정적 집합)
    - ![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/342207fa-44d7-4960-86a9-792665574d6c)
    - 조건 (동적 집합)
    - 상위 (동적 집합)
3. 필터에서 집합 만들기

집합을 행열 선반에 올리느냐, 필터에 올리느냐, 마크 선반에 올리느냐에 따라서 정해진 기본 액션이 있다. 그것이 만약 원하는 형태가 아니라면 마우스 우측클릭으로 IN&OUT으로 표시할 것인지, 멤버로 표시할 것인지 선택하면 된다.

<br>

## 동적 집합 만들기

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/64c05077-79b2-4d27-8996-2b3b96cfa056)

- 수식을 쓸 때에는 집합 생성 대상을 포함하거나 집계 형태로 써야한다.
- 결과는 참과 거짓으로 나뉘어야한다. (Boolean)

<br>

## 결합된 집합

두 개 이상의 집합이 있으면 결합된 집합을 만들 수 있다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/7c0e80be-bb1b-4167-b058-ea963c26148a)

<br>

## 계산식에 집합 사용

집합 자체를 계산식에 쓸 수도 있다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/23b06bcd-23c8-4750-a906-65baff298be0)

### 응용 - 비대칭 드릴다운 I

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/a82d641b-130e-4d17-8179-f30daaa0e947)

만든 계산식으로 다시 집합을 정의한다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/51393649-2267-44b6-908c-293107b97e7e)

다시 제품 중분류(집합)을 이용해 계산식을 만든다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/f2e47754-12ae-4ed9-a6a8-b0b039327b0b)

이후 필드들을 순차적으로 행선반에 가져다놓는다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/1506c024-7f3c-44c0-8e40-fd78e1c4dd8d)

분류를 바꾸고 싶으면 집합 자체를 편집해야 하기에 동적으로 편집하지 못하는 것이 한계점이다.

<br>

## 집합 작업(Set Actions)의 작동 원리

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/2cea11b2-131e-45e3-8186-35dd6d51c717)

### 집합 작업 실습

**선택한 마크가 타겟으로 정의한 집합의 값을 바꾸어준다.**

워크시트 / 대시보드 메뉴 -> 작업

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/168539de-b70f-4501-91ce-391fda1167b1)

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/eb29dd37-61ec-4bf3-8106-46921d0e4cc2)

<br>

원래 의자와 책상이 있었지만, 항목을 선택하고 확인해보면 값이 바뀌어 있는 것을 볼 수 있다.

![image](https://github.com/leejongseok1/leejongseok1.github.io/assets/79849878/90e312c3-f630-4ae8-b21a-040d4c9dfd22)

> 만든 집합 작업 필드를 색상에 가져다 놓아 유용하게 쓸 수 있음

<br>
<br>
<br>

# 📝 과제

<br>