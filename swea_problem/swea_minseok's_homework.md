# swea minseok's homework
5431
- input


```python
2
5 3
2 5 3
7 2
4 6
```

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N, K = map(int, input().split())
    homework_done = list(map(int, input().split()))
    list_people = [0]*(N+1)
    for i in range(N+1):
        for j in range(K):
            if i == homework_done[j]:
                list_people[i] += 1

    ans = []
    for i in range(N+1):
        if list_people[i] == 0:
            ans.append(i)
    ans.pop(0)

    print(f'#{test_case}', *ans)

```
