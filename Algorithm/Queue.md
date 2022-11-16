## **큐(Queue) 란?**

 

큐(Queue)는 **한쪽 끝**에서만 **삽입**이 이루어지고, **다른 한쪽 끝에서는 삭제 연산**만 이루어지는 유한 순서 리스트이다.

![img](https://k.kakaocdn.net/dn/Rcx73/btq0XoA8XYB/Ct5GXjU4SeXp7NMFv7ix4k/img.png)



## **큐(Queue)의 특징 ?**

**First in First Out (FIFO)** 선입선출이라고 생각하면 쉽다. 먼저 들어온 것이 먼저 나가는 형식이다.

즉, 제일 처음에 들어온 데이터가 먼저 삭제가 된다.



## **실생활에서 쓰이는 큐(Queue)의 3가지 예시들**

**1. 티켓 판매부스에서 줄을서서 기다리는 사람들**

![img](https://k.kakaocdn.net/dn/wkpAW/btq01qYLXrP/frEzX6vWKRw48a48GkEK8K/img.jpg)

**2. 한줄로 나란히 가야만하는 차들**



![img](https://k.kakaocdn.net/dn/K8z3g/btq2E8CSeKf/XAnVp2hawwBEJWIMJ22knk/img.jpg)



 

 

**3. 컴퓨터 운영체제의 테스크 스케줄링** 

![img](https://k.kakaocdn.net/dn/we09J/btq2E8pmwNz/5jx47AMvoAJLTqqkoqYgd1/img.png)

## **큐(Queue)의 주요 동작들**

- enQueue() : 큐에 데이터를 넣는다.
- deQueue() : 큐에서 데이터를 빼낸다.
- isEmpty() : 큐가 비어있는지 확인한다.
- isFull() : 큐가 꽉 차 있는지 확인한다.
- peek() : 앞에있는 원소를 삭제하지 않고 반환한다.



## **큐(Queue)의 다른 형식**

#### **원형 큐 (Circle Queue)**

위와 같은 큐의 문제점을 보완하기 위해서 **"원형 큐(Circle Queue)"**를 사용한다.

####  



![img](https://k.kakaocdn.net/dn/CAPCY/btq2Jk2XF9c/y2SMPlLASEHPIv3Hf0Zco0/img.gif)



#### **우선순위 큐 (Priority Queue)** 

우선순위를 이용하여 우선순위가 높은 순서대로 나가게 된다.

쉽게 말해, 병원에서 기존 환자들을 진료 보다가 응급환자가 오게 되면 먼저 진료하게 된다고 이해하면 된다.

 



![img](https://k.kakaocdn.net/dn/do9gP2/btq2IgzXmMl/TCvm6VOwk74a1c3NVbyCBk/img.png)

