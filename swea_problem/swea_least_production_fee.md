# swea least production fee

5209

- input

```
3
3
73 21 21
11 59 40
24 31 83
5
93 4 65 31 66
63 12 60 60 84
87 57 44 35 20
12 9 40 12 40
60 21 3 49 54
6
55 83 32 79 53 70
77 88 80 93 42 29
54 26 5 10 25 94
77 92 82 83 11 51
84 11 21 62 45 58
37 88 13 34 41 4
```

- solve

```python
# 5209

import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    list_arr = list(zip(*arr))
    # print(list_arr[0][0])
    min_num = 100*N
    v = [0]*N

    def solve(row, num):
        global min_num
        if min_num <= num:
            return
        if row == N:
            min_num = min(min_num, num)
        for j in range(N):
            if v[j] == 0:
                v[j] = 1
                solve(row+1, num + arr[row][j])
                # print(v)
                v[j] = 0

    solve(0, 0)
    print(f'#{test_case} {min_num}')

```