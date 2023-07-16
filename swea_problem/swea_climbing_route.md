# climbing route

1949

![image](https://swexpertacademy.com/main/common/fileDownload.do?downloadType=CKEditorImages&fileId=AV5PvGLaAbQDFAUq)

- input

```
10
5 1
9 3 2 3 2
6 3 1 7 5
3 4 8 9 9
2 3 7 7 7
7 6 5 5 8
3 2
1 2 1
2 1 2
1 2 1
5 2
9 3 2 3 2
6 3 1 7 5
3 4 8 9 9
2 3 7 7 7
7 6 5 5 8
4 4
8 3 9 5
4 6 8 5
8 1 5 1
4 9 5 5
4 1
6 6 1 7
3 6 6 1
2 4 2 4
7 1 3 4
5 5
18 18 1 8 18
17 7 2 7 2
17 8 7 4 3
17 9 6 5 16
18 10 17 13 18
6 4
12 3 12 10 2 2
13 7 13 3 11 6
2 2 6 5 13 9
1 12 5 4 10 5
11 10 12 8 2 6
13 13 7 4 11 7
7 3
16 10 14 14 15 14 14
15 7 12 2 6 4 9
10 4 11 4 6 1 1
16 4 1 1 13 9 14
3 12 16 14 8 13 9
3 4 17 15 12 15 1
6 6 13 6 6 17 12
8 5
2 3 4 5 4 3 2 1
3 4 5 6 5 4 3 2
4 5 6 7 6 5 4 3
5 6 7 8 7 6 5 4
6 7 8 9 8 7 6 5
5 6 7 8 7 6 5 4
4 5 6 7 6 5 4 3
3 4 5 6 5 4 3 2
8 2
5 20 15 11 1 17 10 14
1 1 11 16 1 14 7 5
17 2 3 4 5 13 19 20
6 18 5 16 6 7 8 5
10 4 5 4 9 2 10 16
2 7 16 5 8 9 10 11
12 19 18 8 7 11 15 12
1 20 18 17 16 15 14 13

```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

def solve(x, y, path, boolean):
    global count
    if count < path:
        count = path
    for i in range(4):
        new_x = x + dx[i]
        new_y = y + dy[i]
        if new_x < 0 or new_x >= N or new_y < 0 or new_y >= N:
            continue
        if visited[new_x][new_y] == 1:
            continue

        if arr[x][y] > arr[new_x][new_y]:
            visited[new_x][new_y] = 1
            solve(new_x, new_y, path + 1, boolean)
            visited[new_x][new_y] = 0
        elif arr[x][y] <= arr[new_x][new_y] and not boolean:
            for j in range(1, K+1):
                arr[new_x][new_y] -= j
                boolean = True
                if arr[x][y] > arr[new_x][new_y]:
                    visited[new_x][new_y] = 1
                    solve(new_x, new_y, path+1, boolean)
                    visited[new_x][new_y] = 0
                boolean = False
                arr[new_x][new_y] += j

T = int(input())
for test_case in range(1, T+1):
    N, K = map(int, input().split())
    arr = [list(map(int, input().split())) for _ in range(N)]
    dx = [0, 0, 1, -1]
    dy = [1, -1, 0, 0]

    mx = 0
    for i in range(N):
        for j in range(N):
            if mx < arr[i][j]:
                mx = arr[i][j]
    count = 0

    for i in range(N):
        for j in range(N):
            if arr[i][j] == mx:
                visited = [[0] * N for _ in range(N)]
                visited[i][j] = 1
                solve(i, j, 1, False)

    print(f'#{test_case} {count}')
```