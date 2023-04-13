# swea jingi's baking fish

1860

input

```jsx
4
2 2 2
3 4
2 2 2
1 2
2 2 1
4 2
2 2 1
3 2
```

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T + 1):
    N, M, K = map(int, input().split())
    client = list(map(int, input().split()))
    # N : 몇 명 
    # 진수는 M : 초에  K: 개의 붕어빵을 만들 수 있다.
    bread = [0 for _ in range(11112)]

    for i in client:
        bread[i] += 1
    
    ans = 0
    grade = 'Possible'

    for i in range(11112):
        # 0이 되지 않게
        if i != 0 and i%M == 0:
            ans += K
        ans -= bread[i]
        # 손님이 오는 시간에 빼준다.

        if ans < 0:
            grade = 'Impossible'
            break

    print(f'#{test_case} {grade}')
```

다른풀이

```python
T = int(input())
for test_case in range(1, T + 1):
    N, M, K = map(int, input().split())
    client = list(map(int, input().split()))
    count = 0
    ans = 'Possible'
    for t in sorted(client):
        count += 1
        if count > (t//M)*K:
            ans = 'Impossible'
            break
    print(f'#{test_case} {ans}')

```