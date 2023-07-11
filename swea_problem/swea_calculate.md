# calculate

5247

- input

```
3
2 7
3 15
36 1007
```

- 일반적으로 list, pop으로 해결하니 runtime error가 나왔다.
- 이를 해결하기 위해 deque
    - 작은 크기의 list 일 땐 상관없지만
    - 만약 1000000개의 list 에서 맨 앞의 0번째 index 를 삭제한다고 하면 ??? 아주 복잡한 연산이 될 것이다 !
    - list 의 삭제 연산을 약 O(n) 의 시간이 걸리고 deque 의 삭제 연산은 약 O(1) 의 시간이 걸린다

- solve

```python
import sys
sys.stdin = open('sample_input1.txt', 'r')

from collections import deque

def solve(num, count):
    deq = deque([(num, count)])
    visited = set()
    visited.add(num)

    while deq:
        num, count = deq.popleft()

        if num == M:
            return count

        if num * 2 not in visited and num * 2 <= 1000000:
            deq.append((num*2, count+1))
            visited.add(num*2)
        if num + 1 not in visited and num + 1 <= 1000000:
            deq.append((num+1, count+1))
            visited.add(num+1)
        if num - 1 not in visited and 0 <= num - 1:
            deq.append((num - 1, count+1))
            visited.add(num - 1)
        if num - 10 not in visited and 0 <= num - 10:
            deq.append((num - 10, count+1))
            visited.add(num - 10)

T = int(input())

for test_case in range(1, T+1):
    N, M = map(int, input().split())
    ans = solve(N, 0)
    print(f'#{test_case} {ans}')

```