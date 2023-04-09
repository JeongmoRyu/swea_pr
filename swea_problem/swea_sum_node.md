# swea sum node

16533

- input

```python
3
5 3 2
4 1
5 2
3 3
10 5 2
8 42
9 468
10 335
6 501
7 170
17 9 4
16 479
17 359
9 963
10 465
11 706
12 146
13 282
14 828
15 962
```
- solve

```python
import sys
sys.stdin = open('sample_input (1).txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N, M, L = map(int, input().split())

    arr = [list(map(int, input().split())) for _ in range(M)]

    heap = [0] * (N+1)
    for i in range(N+1):
        for j in range(len(arr)):
            if arr[j][0] == i:
                heap[i] = arr[j][1]
    # heap = [0, 0, 0, 3, 1, 2]
    # heap = [0, 0, 0, 0, 0, 0, 501, 170, 42, 468, 335]
    # heap = [0, 0, 0, 0, 0, 0, 0, 0, 0, 963, 465, 706, 146, 282, 828, 962, 479, 359]

    for i in range(N, 0, -1):
        heap[i//2] += heap[i]

    heap[0] = 0

    print(f'#{test_case} {heap[L]}')

```