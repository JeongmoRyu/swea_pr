# swea square room
1861

- input

```python
2
2
1 2
3 4
3
9 3 4
6 1 5
7 8 2
```

1. 문제 생각해보기!!
2. 숫자가 1 커지면 그 점으로 이동한다. n*n 의 0으로 된 보드를 만든다. 
3. 각 숫자에서 커지는 횟수를 보드에 적어준다.
4.  그 숫자 중 제일 큰 숫자들 찾는다
5.  값들이 여러 개이면 그 중 최소를 찾는다.

```python
import sys
sys.stdin = open('s_input.txt', 'r')

T = int(input())
for test_case in range(1, T + 1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]

    count = 0
    check = [0]*(N*N + 1)
    max_count = 0
    dir_x = [-1, 0, 1, 0]
    dir_y = [0, 1, 0, -1]
    # 범위를 정해준다.

    for x in range(N):
        for y in range(N):
            for i in range(4):
                new_x = x + dir_x[i]
                new_y = y + dir_y[i]
                # 이동이 불가능하면 다른 방향 확인
                # x 범위
                if new_x < 0 or new_x >= N:
                    continue
                # y 범위
                if new_y < 0 or new_y >= N:
                    continue
                # 새로운 check에서 연결되었다면 1을 넣어준다.
                if arr[new_x][new_y] == arr[x][y] + 1:
                    check[arr[x][y]] = 1
                    break

    num = 0
    # 제일 큰 순서부터
    for i in range(N*N-1, -1, -1):
        if check[i] == 1:
            count += 1
        # 최대값을 구하기
        else:
            if max_count <= count:
                max_count = count
                num = i+1
        # 아닐 경우를 대비하여
        # count 0으로 다시 복귀
            count = 0

    print(f'#{test_case} {num} {max_count+1}')

```

- bfs 방식

```python
import sys
sys.stdin = open('input.txt', 'r')

def bfs(si, sj):
    # [0] 생성
    q = []
    alst = []
    # 초기 데이터 삽입
    q.append((si, sj))
    v[si][sj] = 1
    alst.append(arr[si][sj])

    while q:
        ci, cj = q.pop(0)
        # 4방향, 미방문, 1차이
        for di, dj in ((-1,0), (1, 0), (0, -1), (0, 1)):
            ni, nj = ci + di, cj + dj
            if 0 <= ni < N and 0 <= nj< N and v[ni][nj]==0 and abs(arr[ci][cj] - arr[ni][nj]) == 1:
                q.append((ni, nj))
                v[ni][nj] = 1
                alst.append(arr[ni][nj])
    return min(alst), len(alst)

T = int(input())
for test_case in range(1, T + 1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    v = [[0]*N for _ in range(N)]
    ans, cnt = N*N, 0
    for si in range(N):
        for sj in range(N):
            if v[si][sj] == 0:
                t, tcnt = bfs(si, sj)
                if cnt < tcnt or cnt == tcnt and ans > t:
                    ans, cnt = t, tcnt

    print(f'#{test_case} {ans} {cnt}')

```