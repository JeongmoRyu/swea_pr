# 주차요금계산

- **요금표**

| 기본 시간(분) | 기본 요금(원) | 단위 시간(분) | 단위 요금(원) |
| --- | --- | --- | --- |
| 180 | 5000 | 10 | 600 |
- **입/출차 기록**

| 시각(시:분) | 차량 번호 | 내역 |
| --- | --- | --- |
| 05:34 | 5961 | 입차 |
| 06:00 | 0000 | 입차 |
| 06:34 | 0000 | 출차 |
| 07:59 | 5961 | 출차 |
| 07:59 | 0148 | 입차 |
| 18:59 | 0000 | 입차 |
| 19:09 | 0148 | 출차 |
| 22:59 | 5961 | 입차 |
| 23:00 | 5961 | 출차 |
- **자동차별 주차 요금**

| 차량 번호 | 누적 주차 시간(분) | 주차 요금(원) |
| --- | --- | --- |
| 0000 | 34 + 300 = 334 | 5000 + ⌈(334 - 180) / 10⌉ x 600 = 14600 |
| 0148 | 670 | 5000 +⌈(670 - 180) / 10⌉x 600 = 34400 |
| 5961 | 145 + 1 = 146 | 5000 |

```jsx
import math

def solution(fees, records):
    check = {}

    for record in records:
        time, number, Inout = record.split()
        time = time.split(':')
        time = int(time[0])*60 + int(time[1])
        if number not in check:
            check[number] = (0, time, Inout)
        if Inout == 'IN':
            check[number] = (check[number][0], time, Inout)
        elif Inout == 'OUT':
            totalTime, inTime, _ = check[number]
            totalTime += time - inTime
            check[number] = (totalTime, time, Inout)

    result = {}

    for number in check.keys():
        totalTime, time, Inout = check[number]
        if Inout == 'IN':
            totalTime += 1439 - time
        fee = fees[1]
        if totalTime <= fees[0]:
            result[number] = fee
        else:
            fee = fee + math.ceil((totalTime - fees[0]) / fees[2]) * fees[-1]
            result[number] = fee
        
        sortedList = sorted(result.items())
        answer = []
        for i in range(len(sortedList)):
            answer.append(sortedList[i][1])
    return answer
```

이렇게도 정렬을 하던데 신기방기

```jsx
        sortedList = list(map(lambda x:x[1], sorted(result.items())))
```
