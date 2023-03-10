# swea_snail_numbering 16307

## snail_numbering

input

```python
3
3
1 2 3 5 6 7 10 11 12
4
2 4 6 8 10 1 3 5 7 9 11 13 14 12 16 20
5
289 625 324 484 25 9 100 121 169 441 256 576 225 196 1 144 529 81 36 49 64 4 16 361 400
```

```python

import sys

sys.stdin = open('input.txt')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    list_num = list(map(int, input().split()))
    arr = [[0 for _ in range(N)] for _ in range(N)]
    # 순서대로 정렬된 새 리스트를 만든다.
    list_new_num = sorted(list_num)

    x = 0
    y = 0
    arr[x][y] = list_new_num[0]
    # 우, 하, 좌, 상 순으로 방향 전환이 계속된다.
    delta_x = [0, 1, 0, -1]
    delta_y = [1, 0, -1, 0]
    # 이동하는 방향에 따른 좌표 이동을 표현한다. 우, 하, 좌, 상
    dir_idx = 0
    count = 1

    while count < N**2:
        # 2차원 사각형에서 총 갯수는 N의 제곱이므로 N의 제곱까지 while로 지속시켜준다.
        new_x = x + delta_x[dir_idx]
        new_y = y + delta_y[dir_idx]
        # 다음 좌표 (new_x, new_y)가 아직 사각형 안에 있는지 확인
        # 이전에 방문한 적이 없는지 확인
        if (0 <= new_x < N and 0 <= new_y < N) and arr[new_x][new_y] == 0:
            arr[new_x][new_y] = list_new_num[count]

            # 숫자 추가
            # 새 위치를 갱신한다.
            x, y = new_x, new_y
            count += 1
            #다음 쓸 숫자
        elif dir_idx == 3:
            # 4가지 방향성을 다 사용하였다면 다시 우방향으로 변화시킨다.
            dir_idx = 0
        else:
            dir_idx += 1
            # 범위가 넘어가게 되면 다음 방향으로 전환하는 것을 실행시켜준다.
            # 우하좌상 순서대로 진행시켜준다.
    print(f'#{test_case}')
    for i in range(N):
        for j in range(N):
            print(arr[i][j], end = ' ')
        print()
```