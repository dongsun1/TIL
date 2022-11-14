# 스택이란?

**스택의 개념**

- 메모리의 스택 영역은 함수의 호출과 관계되는 지역변수, 매개변수, 리턴 값등의 임시데이터를 저장한다.
- 스택이란 단어는 ‘차곡 차곡 쌓여진 더미’를 의미한다.
- LIFO(Last In First Out, 후입선출) 구조라고도 한다.

 



**스택의 구조**

- 가장 먼저 저장되는 데이터는 스택의 아래 쪽(높은 주소)부터 쌓이고, 다음 저장되는 데이터가 바로 그 위(낮은 주소)에 쌓인다.

 

이제부터 스택 영역에 새로운 데이터가 추가되고 사용되는 모습의 예를 살펴보겠다.

![img](https://t1.daumcdn.net/cfile/tistory/99AF81395BB1D8212B)

스택에 새로운 데이터를 추가하는 것을 PUSH라고 한다.

PUSH를 하면 기존 데이터 위에 새 데이터가 순서대로 쌓인다.

![img](https://t1.daumcdn.net/cfile/tistory/99A10C4A5BB1D83C0F)

스택에 있던 데이터를 다시 빼내는 것을 POP이라고 한다.

 

이처럼 스택은 기본적으로 PUSH와 POP을 통해 데이터의 추가/제거가 가능하며 이 PUSH/POP 되는 데이터의 크기는 프로그래머가 정할 수 있다.

 

이처럼 스택이  데이터를 추가하는 이유는 커널 영역을 침범하지 않기 위해서 밑에서부터 데이터를 추가한다. 



**스택의 TOP & BOTTOM**

- TOP/BOTTOM은 스택의 특정 위치를 가리킵니다.

- TOP는 가장 최근에 스택에 저장된 값, BOTTOM은 가장 처음 스택에 저장된 값을 가리킵니다.

![img](https://t1.daumcdn.net/cfile/tistory/991F52425BB1D8592D)

현재 이 그림에서는 TOP/BOTTOM의 위치와 다음과 같다.

![img](https://t1.daumcdn.net/cfile/tistory/99A2054C5BB1D8711A)

여기서 C라는 데이터가 PUSH가 되면 TOP/BOTTOM의 위치는 어떻게 될까?

![img](https://t1.daumcdn.net/cfile/tistory/990CB7465BB1D89123)

아까 TOP은 B를 가리켰지만 현재는 C를 가리키고 있다.

BOTTOM은 그대로이다.

 

BOTTOM의 위치는 항상 스택 가장 아랫값을 가리키고 있기 때문에 고정된다. 하지만 TOP의 위치는 데이터가 추가되거나, 데이터가 제거될 때 마다 달라진다.