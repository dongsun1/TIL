# ES Module 이란?

ES 모듈은 자바스크립트의 공식 모듈이다.
그렇다면 자바스크립트 모듈은 무엇일까?

### Javascript Module 이란?

자바스크립트 모듈을 알기 위해 이해해야 할 과정이 있다.

1. 기존의 웹은 자바스크립트의 비중이 크지 않았고, 따라서 큰 스크립트가 필요하지 않았다.
2. 웹의 발전에 따라 점점 자바스크립트의 중요도가 커지고, 여러 스크립트 파일을 쓰며 상호작용해야 했다.
3. 이를 처리하기 위해 JQuery 등으로 해결했지만 여러 문제점이 발생했다.
4. 이에 따라 각 파일 간의 상호작용을 위해 모듈화한다.

Node.js에선 이미 CommonJS와 같은 모듈 시스템이 존재했고, ES module은 자바스크립트 최신 모듈 시스템이다.

# 왜 사용하는가?

### brower에서의 ESM

#### 기존의 문제점

- 초기 자바스크립트는 독립적인 작업을 수행하며 큰 스크립트가 필요하지 않았다. 

- jQuery가 생겨나고 어플리케이션의 규모가 커지면서 script파일을 나누기 시작했고, 파일간의 변수, 함수 등을 전달하고 받는 방법이 필요했다.

- ESM 이전에는 각각의 script 파일을 전역 스코프처럼 사용했다. 

- HTML 파일에서 보다 위에 있는 script 파일은 전역 스코프처럼 하위의 script 태그에서 접근, 변경이 가능했다.

- 이 때문에 jQuery script를 최상단에 두고, 순서를 올바르게 구성하는게 중요했다.
  - 이 구조는 파일 순서가 뒤틀리면 에러가 발생하고,
  - 하위 script가 상위 script의 값을 쉽게 변경시키는 '전역 오염'이 발생하기 쉬우며,
  - 해당 script가 어떤 script에 의존성을 갖고 있는지 파악하기 힘들다.
  - 즉, 유지보수가 힘들다.

#### 해결책 - 모듈화

- 이러한 문제속에서 모듈화에 대한 필요성이 높아져 ES Module이 등장하게 되었다.

- 모듈은 함수와 변수를 모듈 스코프에 넣고, 각 함수는 함수 스코프를 가진다.

- 다만 export로 해당 변수, 함수를 "다른 모듈에서 import를 통해 의존할 수 있도록" 지정할 수 있다.

- 이러한 모듈화는 다음과 같은 장점을 가진다.
  - import - export의 명시적 관계로, 하나의 모듈이 제거되면 어떤 모듈이 손상되었는지 알 수 있다. 
  - 즉, 의존성 파악에 용이하다.(A가 import B를 하고 있을 때, B가 사라지거나 오류가 생기면 not found B 에러가 뜨는 등)
  - 코드들을 각각 독립적으로 작동할 수 있는 단위로 나누기 수월하다. 이는 모듈을 재사용함으로써 다양한 종류의 어플리케이션을 만들 수도 있다.
  - import - export로 관계되지 않은 모듈간의 오염은 일어나지 않는다.

# 모듈은 어떻게 동작하는 걸까?

#### ES 모듈의 진행 순서 3단계

![img](https://velog.velcdn.com/images/yoonlang/post/8687ee06-e1a6-49c7-94f8-4ffbd9a085a4/image.png)

#### 1. 구성

1. 모듈이 들어있는 파일을 어디서 다운 받을 것인지 확인

2. 파일 가져오기 (URL or File system)

   진입점 파일 찾기

   ```javascript
   <script src="main.js" type="module">
   ```

   type="module"을 통해 진입점을 확인한다.

   다음 모듈은 import를 통해 찾을 수 있다.

   ![img](https://velog.velcdn.com/images/yoonlang/post/7d96712b-7b38-4dcc-93a4-6086539ec751/image.png)

3. 파일 구문 분석

#### 2. 인스턴스 화

이제 import와 export한 것들이 메모리에 연결되어야 한다. 먼저 export부터 연결하는데, 모듈 그래프를 인스턴스 화하기 위해 **깊이 우선 탐색**을 한다.

모든 의존의 최하단까지 도달 후 export를 설정한다. 그 후 import를 연결한다.

![img](https://velog.velcdn.com/images/yoonlang/post/76142235-6156-4007-a3d6-94cbf41df1c8/image.png)

![img](https://velog.velcdn.com/images/yoonlang/post/32e3cce1-2092-4890-9de2-b31718954561/image.png)

**라이브 바인딩이란?**

Node.js의 모듈 시스템인 CommonJS는 위의 인스턴스 과정에서 export 객체가 메모리에 올라갈 때, 복제된 값이 올라간다. 따라서 인스턴스 과정이 끝나고, export 하는 모듈에서 값 수정이 일어나도 import 하는 모듈에선 알 수 있는 방법이 없다. 이에 반해 ES 모듈은 **라이브 바인딩**을 사용한다. 위 사진처럼 export 하는 모듈과 import 하는 모듈이 같은 메모리 주소에 접근한다.

#### 3. 평가

메모리에 값을 부여하는 단계
평가 단계에서 한 모듈은 한 번만 평가한다.

평가 단계는 코드를 실행하는 단계인데, 여러 번 실행하게 되면 값이 변경될 수도 있기 때문. 따라서 이를 처리하기 위해 **모듈맵**을 이용하여 깊이 우선 탐색을 통해 처리한다.

**모듈맵**

자료구조 map을 떠올리면 된다. 모듈들을 URL을 통해 관리한다.

![img](https://velog.velcdn.com/images/yoonlang/post/4adfd4b5-4e3e-4770-9cfa-d8db5981330f/image.png)

### ES Module은 순환 의존성을 지원한다

앞서 말했듯 ES Module에서는 라이브 바인딩을 사용한다. 따라서 순환 구조가 발생해도 빈 객체를 반환한다. 하지만 CommonJS는 라이브 바인딩이 아니고 사본을 메모리에 넣기 때문에 사이클이 생기면 처리할 수 없다.

![img](https://velog.velcdn.com/images/yoonlang/post/1d649b05-c6b9-4d27-8b98-7522197c978d/image.png)