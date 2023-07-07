# swimming pool 
1952 / 14119


![Untitled](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F5t8Nq%2FbtrajQgG8P8%2FjpDh68fti9RbmaiWnuQkO0%2Fimg.png)

![Untitled](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbq1Wyu%2FbtranVVlkgI%2FtP5KPsHzYO2HcrThKww6C1%2Fimg.png)

- input

```
10
10 40 100 300
0 0 2 9 1 5 0 0 0 0 0 0
10 100 50 300
0 0 0 0 0 0 0 0 6 2 7 8
10 70 180 400
6 9 7 7 7 5 5 0 0 0 0 0
10 70 200 550
0 0 0 0 8 9 6 9 6 9 8 6
10 80 200 550
0 8 9 15 1 13 2 4 9 0 0 0
10 130 360 1200
0 0 0 15 14 11 15 13 12 15 10 15
10 180 520 1900
0 18 16 16 19 19 18 18 15 16 17 16
10 100 200 1060
12 9 11 13 11 8 6 12 8 7 15 6
10 170 500 1980
19 18 18 17 15 19 19 16 19 15 17 18
10 200 580 2320
12 28 24 24 29 25 23 26 26 28 27 22
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

def dfs(n, sm):
    global ans
    if ans <= sm:
        return

    if n > 12:
        ans = min(ans, sm)
        return
    dfs(n+1, sm + day*lst[n])
    dfs(n+1, sm+month)
    dfs(n+3, sm+three_month)
    dfs(n+12, sm+year)

T = int(input())
for test_case in range(1, T+1):
    day, month, three_month, year = map(int, input().split())
    lst = [0] + list(map(int, input().split()))

    ans = 365 * 3000
    dfs(1, 0)
    print(f'#{test_case} {ans}')
```