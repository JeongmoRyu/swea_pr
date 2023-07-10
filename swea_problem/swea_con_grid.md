# swea con grid

14035

2819

- input

```
1
1 1 1 1
1 1 1 2
1 1 2 1
1 1 1 1

```

- solve

```python
# 14035
# 2819
import sys
sys.stdin = open('sample_input.txt', 'r')

def dfs(n, num, ci, cj):
    if n == 7:
        if num not in list_ans:
            list_ans.append(num)
        return

    for di, dj in [[-1, 0], [1, 0], [0, -1], [0, 1]]:
        ni, nj = ci+di, cj+dj
        if 0 <= ni < 4 and 0 <= nj < 4:
            dfs(n + 1, num * 10 + arr[ni][nj], ni, nj)

T = int(input())
for test_case in range(1, T+1):
    N = 4
    arr = [list(map(int, input().split())) for _ in range(N)]
    list_ans = []
    for i in range(4):
        for j in range(4):
            dfs(1, arr[i][j], i, j)

    ans = len(list_ans)
    print(f'#{test_case} {ans}')
```

- solve(set을 써서 쉽게 푸는 방법)

```python
# 14035
# 2819
import sys
sys.stdin = open('sample_input.txt', 'r')

def dfs(n, tst, ci, cj):
    if n==7:
        sset.add(tst)
        return

    for di, dj in ((-1, 0), (1, 0), (0, -1), (0, 1)):
        ni, nj = ci+di, cj+dj
        if 0<= ni < 4 and 0 <= nj < 4:
            dfs(n+1, tst*10+arr[ni][nj], ni, nj)

T = int(input())
for test_case in range(1, T+1):
    N = 4
    arr = [list(map(int, input().split())) for _ in range(N)]
    sset = set()
    for i in range(4):
        for j in range(4):
            dfs(1, arr[i][j], i, j)

    ans = len(sset)
    print(f'#{test_case} {ans}')
```