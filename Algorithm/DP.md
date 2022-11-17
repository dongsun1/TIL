## **동적 계획법이란?**

 

DP (Dynamic Programming)는 코딩 테스트의 절반 이상을 차지하는 알고리즘이라 봐도 무방하다.

 

DP는 분할 정복과 매우 유사하다.

하지만 분할 정복은 top-down 방식을 이용하고, DP는 bottom-up 방식을 이용합니다.

가장 작은 instance의 답을 먼저 구하여 저장하고, 필요하면 꺼내 쓰는 '동적 계획'이다.

 

여기서 계획이란 문제 해결을 위한 배열(테이블)을 구축한다는 뜻이다.

 

DP 알고리즘의 개발 절차는 다음과 같다.

1. **문제의 instance의 해답을 구하는 재귀 관계식을 세운다. (top-down approach, Divide and Conquer 방식)**
2. **작은 instance부터 해결하는 bottom-up 방법으로 전체 instance에 대한 해답을 찾는다.**

즉 Divide and Conquer로 문제를 해결한 다음, 중복 계산 문제가 있는지를 확인한다.

이후, 중복 계산 문제를 해결하기 위해 배열을 이용해 저장하는 **Memoization**을 사용한다.

그다음에는 이제 재귀 문제를 해결하기 위해 반복문으로 해결하는 **Tabulation**을 사용한다.

![img](https://k.kakaocdn.net/dn/AeLfC/btrzi3CCgsU/7wkfKtApkQfslcuz3VXTS0/img.png)

- **Divide and Conquer(중복 계산 문제, 재귀)**
- **Memoization(중복 계산 문제 제거, 재귀)**
- **Tabulation(중복 계산 문제 제거, 재귀 제거, 반복문)**

결국 Tabulation이 최종 결과물이 되어야 한다.