# 해시 테이블

컴퓨팅에서 키를 값에 매필할 수 있는 구조인, 연관 배열 추가에 사용되는 자료구조.

해시 테이블은 해시 함수를 사용하여 색인(index)을 버킷(bucket)이나 슬롯(slot)의 배열로 계산한다.

데이터를 다루는 기법 중에 하나로 데이터의 검색과 저장이 아주 빠르게 진행된다.

# 해시 테이블의 장점

- 어떤 것과 다른 것 사이의 관계를 모형화할 수 있다.
- 중복을 막을 수 있다. (충돌을 피하는 설계를 하게 되니 가장 이상적이다)
- 서버에 작업을 시키지 않고 자료를 캐싱할 수 있다.

# 해시 테이블의 사용 예시

- 전화번호부 (이름 : 전화번호)
- 메뉴판 (메뉴 : 가격)

# 충돌

해시 함수는 보통 입력값의 범위보다 출력 값의 범위가 좁은 경우가 많다.

그래서 입력값이 달라져도 드물게 동일한 출력 값이 나오는 경우가 있다.

이러한 경우를 충돌이라고 한다.

해시 함수는 원칙적으로 이런 어쩔 수 없는 충돌을 제외하고는 의도적으로 충돌을 계산해낼 수 없어야 한다.

그래서 해시 함수의 질은 이러한 해시 충돌 확률로 결정된다.

해시 충돌의 확률이 높을수록 서로 다른 데이터를 구별하기 어려워지고 검색하는 비용이 증가하게 된다.