# Cron 표현식

Cron 표현식이란 스케줄러의 정규 표현식이다.

7개의 각 필드로 구성되어 있으며, 각 필드의 내용은 아래와 같다.

|    필드명    |    값의 허용 범위    | 허용된 특수문자 |
| :----------: | :------------------: | :-------------: |
| 초 (Seconds) |        0 ~ 59        |    , - \* /     |
| 분 (Minutes) |        0 ~ 59        |    , - \* /     |
|  시 (Hours)  |        0 ~ 23        |    , - \* /     |
|   일 (Day)   |        1 ~ 31        | , - \* ? / L W  |
|  월 (Month)  | 1 ~ 12 or JAN ~ DEC  |    , - \* /     |
| 요일 (Week)  |  0 ~ 6 or SUN ~ SAT  | , - \* ? / L W  |
| 연도 (Year)  | empty or 1970 ~ 2099 |    , - \* /     |

# 특수문자

- '\*' : 모든 값
- '?' : 특정한 값이 없음
- '-' : 범위 ex) 월요일에서 수요일까지는 MON-WED로 표현
- ',' : 특별한 값일 때만 동작 ex) MON, WED, FRI
- '/' : 시작시간 / 단위 ex) 0분부터 매 5분 => 0/5
- 'L' : 일에서 사용하면 마지막 일, 요일에서는 마지막 요일(토요일)
- 'W' : 가장 가까운 평일 ex) 15W는 15일에서 가장 가까운 평일 (월 ~ 금)
- '#' : 몇째주의 무슨 요일을 표현 ex) 3#2 : 2번째 주 수요일
