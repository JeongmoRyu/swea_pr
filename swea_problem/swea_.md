# swea deltasearch 16258

- input
```
3
5
45 15 10 56 23
96 98 99 40 69
96 84 49 46 34
16 64 81 4 11
10 66 85 55 14
5
44 91 64 73 62
78 72 52 73 48
44 88 55 75 24
22 72 59 26 62
87 11 64 79 40
5
10 10 10 10 10
10 10 10 10 10
10 10 10 10 10
10 10 10 10 10
10 10 10 10 10
```


- solve

```python
import sys
sys.stdin = open("../in.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    arr = []
    for _ in range(N):
        arr.append(list(map(int, input().split())))

    dx = [-1, 1, 0, 0]
    dy = [0, 0, -1, 1]
    # 상하좌우의 방향성에 따라 위치값들을 정해준다.
    # directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]

    # arr = [list(map(int, input().split())) for _ in range(N)]
    # 한줄로도 표현 가능하다.
    # for item in arr:
    #   print(item)
    # 보기 편하게도 바꿀 수 있다.
    total_sum = 0
    for i in range(N):
        # i는 y값이다.
        for j in range(N):
    # j는 x값이다.
            this_sum = 0
            # print(f'i: {i}, j: {j}, arr[i][j]: {arr[i][j]}')
            for dir in range(4):
                    cmp_x = j + dx[dir]
                    cmp_y = i + dy[dir]
                    if 0 <= cmp_x < N and 0 <= cmp_y < N:
                    # 범위 이외의 값들을 제거해주자
                        this_sum += abs(arr[i][j] - arr[cmp_y][cmp_x])
                    # 절대값 abs
            total_sum += this_sum

    print(f'#{test_case} {total_sum}')
```