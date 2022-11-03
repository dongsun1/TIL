# 이진 탐색 (Binary search) 개념 및 구현

이진 탐색은 정렬된 리스트에서 검색 범위를 줄여 나가면서 검색 값을 찾는 알고리즘이다.



이진 탐색은 정렬된 리스트에만 사용할 수 있다는 단점이 있지만, 검색이 반복될 때마다 검색 범위가 절반으로 줄기 때문에 속도가 빠르다는 장점이 있다.

#### 동작 방식

이진 탐색 알고리즘은 리스트의 중간 값과 비교하여 검색 값을 찾는다.

중간 값을 찾아야 하기 때문에 반드시 정렬된 배열에서만 사용할 수 있다.

 

이진 탐색의 동작 방식은 다음과 같다. 

1. 배열의 중간 값을 가져온다.
2. 중간 값과 검색 값을 비교한다.
   1. 중간 값이 검색 값과 같다면 종료한다. (mid = key)
   2. 중간 값보다 검색 값이 크다면 중간 값 기준 배열의 오른쪽 구간을 대상으로 탐색한다. (mid < key)
   3. 중간 값보다 검색 값이 작다면 중간 값 기준 배열의 왼쪽 구간을 대상으로 탐색한다. (mid > key)
3. 값을 찾거나 간격이 비어있을 때까지 반복한다.

#### 검색 예

이진 탐색을 사용하여 key = 32 값을 찾는 과정을 보도록 하겠다.

1. 먼저 배열의 가운데를 결정한다.

```
mid  = low + (high - low) / 2
          = 0 + (9-0)/2
          = 4
```

![img](https://k.kakaocdn.net/dn/cqSVub/btq5lyj0hdx/uueqouAwXkPUcQGJrFgEo0/img.png)

2. 중앙 값과 검색 값을 비교한다. 

   A [4] < key 이므로 배열의 오른쪽 구간을 검색 범위로 정한다.

```
low = mid + 1
        = 4 + 1
        = 5
```

![img](https://k.kakaocdn.net/dn/3SLNJ/btq5ffT6iar/WLKlWZO792tJTWVVNbXP5K/img.png)

3. 중앙 값을 결정한다.

```
mid = 5+ (9-5)/2
         = 7
```

![img](https://k.kakaocdn.net/dn/cTdRoI/btq5fDmvXe8/5zi2DU9psPgWYAVaLcZvGK/img.png)

4. 중앙 값과 검색 값을 비교한다.

   A [7] > key 이므로 배열의 왼쪽 구간을 탐색 범위로 정한다.

```
high = mid -1
          = 7 - 1
          = 6
```

![img](https://k.kakaocdn.net/dn/KjVE5/btq5gvPmCiP/uTyoNRu1MuoKkgXpGb6ckK/img.png)

5. 중앙 값을 결정합니다.

```
mid = 5 + (6-5)/2
         = 5
```

![img](https://k.kakaocdn.net/dn/0vmuK/btq5gvBOldB/xeNJojg5kJyJpFNi3jL3t1/img.png)

6. 중앙 값과 검색 값을 비교합니다.

   A [5] = key 이므로 탐색을 종료합니다.

#### 시간 복잡도

| Operation | Best | Average  | Worst    |
| --------- | ---- | -------- | -------- |
| Search    | O(1) | O(log n) | O(log n) |

*n = 데이터 수

#### 종료 조건

이진 탐색의 종료 조건은 두 가지가 있다. 다음 조건 중 하나라도 성립하면 검색을 종료한다.

1. 검색을 성공할 경우

- 리스트에서 검색할 값과 같은 요소를 발견한 경우
- a [mid] == key

![img](https://k.kakaocdn.net/dn/EZfk8/btq5ffsWrSC/ISKOrApAubQrddI0WxYCuk/img.png)

2. 검색을 실패한 경우

- 더 이상 검색할 범위가 없을 경우
- low > high

![img](https://k.kakaocdn.net/dn/u6MTp/btq5nbhLRfO/U66KTWbCgzh6Cq3780ZgN0/img.png)

#### 구현

```js
const binarySearch = (list, target, left, right) => {
  let mid = 0;

  while (left <= right) {
    // 가운데 인덱스
    mid = Math.floor((left + right) / 2);

    if (list[mid] === target) {
      return mid;
    }
    
    // 대소 비교로 범위 지정
    if (list[mid] > target) {
      right = mid - 1;
    } else {
      left = mid + 1;
    }
  }

  return -1;
}

const sample = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

sample.sort((a, b) => a - b);

// ( 찾을 배열, 탐색할 값, 시작점, 끝점 )
const result = binarySearch(sample, 7, 0, sample.length - 1);

console.log(result);
```

