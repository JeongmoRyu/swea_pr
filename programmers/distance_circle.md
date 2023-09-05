# distance_circle

- 시간 초과 나는 풀이 6개 까지 빠르게 되는데 ㅠㅠ
    - 처음에는 가장 원초적으로 r1**2 ≤ i**2 + j**2 ≤ r2**2으로 풀어보았는데 더 많은 정답이 시간초과가 발생하였다.
    - 그래서 4분면을 나누고 루트로 변환시켜서 해결해보았지만 fail

```python
def solution(r1, r2):
    answer = 0

    for i in range(1, r2 + 1):
        for j in range(1, r2+1):
            if r1 <= (i**2 + j**2)**(1/2) <= r2:
                answer += 1
    answer += (r2 - r1) + 1
    answer *= 4
    return answer
```

- for 문 두번을 쓰지 않는 방법을 찾아야 했고 거리만을 이용해서 구하는 방법을 찾아보았다.
    - 시간 단축을 위해서 math를 사용하였다.

```python
def solution(r1, r2):
    import math
    answer = 0

    for i in range(1, r2 + 1):
        x = math.sqrt(r2**2 - i**2)
        y = 0
        if i <= r1:
            y = math.sqrt(r1**2 - i**2)
        answer += math.floor(x) - math.ceil(y) + 1
    answer *= 4

    return answer
```
