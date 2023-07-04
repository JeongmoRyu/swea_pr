# swea_dongchul's_work

1865

- sample_input

```python
1
3
13 0 50
12 70 90
25 60 100
```

- solve

```python
import sys
sys.stdin = open('input (1).txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    # print(arr)
    max_num = -1
    visited = [0]*N

    def solve(row, num):
        global max_num
        if max_num >= num:
            return
        if row == N:
            max_num = max(max_num, num)
        for j in range(N):
            if visited[j] == 0:
                visited[j] = 1
                solve(row + 1, num * arr[row][j] * 0.01)
                visited[j] = 0

    solve(0, 1)
    ans = format(max_num*100, ".6f")
    print(f'#{test_case} {ans}')

```