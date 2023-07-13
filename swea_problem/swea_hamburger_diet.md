# hamburger diet

5215

- input

```
1
5 1000
100 200
300 500
250 300
500 1000
400 400
```

- solve

```python
import sys
sys.stdin = open('sample_input2.txt', 'r')

def solve(count, start, mx, kal):
    global ans
    if mx > ans:
        ans = mx
    if count == N:
        return
    for i in range(start, N):
        if kal + arr[i][1] <= L:
            solve(count + 1, i + 1, mx + arr[i][0], kal + arr[i][1])

T = int(input())
for test_case in range(1, T+1):
    N, L = map(int, input().split())
    arr = [list(map(int, input().split())) for _ in range(N)]
    ans = 0
    solve(0,0,0,0)
    print(f'#{test_case} {ans}')

```