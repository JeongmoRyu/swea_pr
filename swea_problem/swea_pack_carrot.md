# swea pack carrot

16811

- input

```python
3
3
1 2 3
5
1 1 1 2 3
8
1 2 3 4 5 6 7 8
```

- solve

```python
import sys
sys.stdin = open('input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = list(map(int, input().split()))

    arr.sort()

    minV = 1000
    for i in range(N-2):
        for j in range(i+1, N-1):
            if arr[i] != arr[i+1] and arr[j] != arr[j+1]:
                A = i + 1
                B = j - i
                C = N - 1 - j
                if A*B*C != 0 and A <= N//2 and B <= N//2 and C <= N//2:
                    if minV > max(A, B, C) - min(A, B, C):
                        minV = max(A, B, C) - min(A, B, C)
    if minV == 1000:
        minV = -1
    print(f'#{test_case} {minV}')
```

다른 풀이

```python

import sys
sys.stdin = open('sample_in.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = list(map(int, input().split()))

    minV = 1000

    size = [0] * 31
    for c in arr:
        size[c] += 1
    print(size)

    for i in range(29):
        for j in range(30):
            A = sum(size[1:i+1])
            B = sum(size[i+1:j+1])
            C = sum(size[j+1:31])

            if A*B*C != 0 and A<=N//2 and B<=N//2 and C<=N//2:
                diff = max(A, B, C) - min(A, B, C)
                print(diff, A, B, C)
                # print(diff)
                if minV > diff:
                    minV = diff
    if minV == 1000:
        minV = -1
    print(f'#{test_case} {minV}')
```