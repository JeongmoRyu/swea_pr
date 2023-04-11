# swea protecting system

2117

input

```python
10
8 3
0 0 0 0 0 1 0 0
0 1 0 1 0 0 0 1
0 0 0 0 0 0 0 0
0 0 0 1 0 1 0 0
0 0 1 1 0 0 0 0
0 0 0 0 0 0 0 0
0 0 0 0 1 0 1 0
1 0 0 0 0 0 0 0

...
```

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

def solve_loop():
    mx = 0
    for si in range(N):
        for sj in range(N):
            for k in range(1, 2*N):
                cnt = 0
                for i in range(si-k+1, si+k):
                    t = abs(si - i)
                    for j in range(sj-k+1+t, sj+k-t):
                        if 0<=i<N and 0<=j<N:
                            cnt += arr[i][j]
                # 운영비용 보다 수익이 같거나 큰 경우 정답 갱신
                if ((k*k)+((k-1)*(k-1))) <= cnt*M:
                    mx = max(mx, cnt)
    return mx

T = int(input())

for test_case in range(1, T + 1):
    N, M = map(int, input().split())
    arr = [list(map(int, input().split())) for _ in range(N)]

    ans = solve_loop()
    print(f'#{test_case} {ans}')
```

다른 풀이 방식

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

# k : 범위, houses : 집 리스트, city_size : N, margin : 지불비용
def check_profit(k, houses, city_size, margin):
    result = 0
    cost = k**2 + (k-1)**2

    # 모든 지점에서 서비스 시도
    for i in range(city_size):
        for j in range(city_size):
            house_count = 0
            for house_x, house_y in houses:
                # 이 지점에서 도달 가능한 집일 때
                if abs(i - house_x) + abs(j - house_y) <= k-1:
                    house_count += 1

            profit = house_count * margin - cost
            # 이득이 남고, 가장 많은 집에 서비스 제공
            if profit >= 0:
                result = max(result, house_count)

    return result

T = int(input())

for test_case in range(1, T + 1):
    N, M = map(int, input().split())
    # houses = [list(map(int, input().split())) for _ in range(N)]
    houses = []
    for i in range(N):
        line = list(map(int, input().split()))
        for j in range(N):
            if line[j]:
                houses.append((i, j))

    result = 0
    for k in range(N+2, 0, -1):
        result = max(check_profit(k, houses, N, M), result)

    print(f'#{test_case} {result}')
```

bfs 방식으로 풀기

```python
정답이 아니지만....
위의 풀이에서 solve를 변형해서 가져온다면?
import sys
# sys.stdin = open('sample_input.txt', 'r')
#
# cost = [((k*k)+(k-1)*(k-1)) for k in range(40)]
#
# def bfs(si, sj):
#     q = []
#     v = [[0]*N for _ in range(N)]
#     old = 0
#     mx = 0
#     q.append((si, sj))
#     v[si][sj] = 1
#     cnt = arr[si][sj]
#
#     while q:
#         ci, cj = q.pop(0)
#         # k 값이 달라진경우
#         if old != v[ci][cj]:
#             old = v[ci][cj]
#             if cost[v[ci][cj]] <= cnt*M:
#                 mx = max(mx, cnt)
#
#         for di, dj in ((-1,0), (1, 0), (0, 1), (0,-1)):
#             ni, nj = ci + di, ci+dj
#             if 0<=ni<N and 0<=nj<N and v[ni][nj] == 0:
#                 q.append((ni, nj))
#                 v[ni][nj] = v[ci][cj] + 1
#                 cnt += arr[ni][nj]
#     return mx
#
#
# def solve_bfs():
#     mx = 0
#     for si in range(N):
#         for sj in range(N):
#             mx = max(mx, bfs(si, sj))
#
#     return mx
#
# T = int(input())
#
# for test_case in range(1, T + 1):
#     N, M = map(int, input().split())
#     arr = [list(map(int, input().split())) for _ in range(N)]
#
#     ans = solve_bfs()
#     print(f'#{test_case} {ans}')
```