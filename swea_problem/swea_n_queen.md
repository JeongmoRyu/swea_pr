# swea n queen

2806

- input

```python
2
1
2
```

- solve

```python

import sys
sys.stdin = open('sample_input1.txt', 'r')

def promising(p, q):
    for di, dj in [[-1 , -1], [-1 , 0], [-1 , 1]]:
        ni, nj = p + di, q + dj
        while 0 <= ni < N and 0 <= nj < N:
            if board[ni][nj]:
                return 0
            ni, nj = ni + di, nj + dj
    return 1

def f(i, N):
    global count
    if i == N:
        count += 1
    else:
        for j in range(N):
            if promising(i, j):
                board[i][j] = 1
                f(i+1, N)
                board[i][j] = 0

T =int(input())
for test_case in range(1, T+1):
    N = int(input())
    board = [[0]*N for _ in range(N)]
    count = 0
    f(0, N)
    print(f'#{test_case} {count}')
```

- input 10 output 10

```
10
1
2
3
4
5
6
7
8
9
10

```

```python
#1 1
#2 0
#3 0
#4 2
#5 10
#6 4
#7 40
#8 92
#9 352
#10 724
```