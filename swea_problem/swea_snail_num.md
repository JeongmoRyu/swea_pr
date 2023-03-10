# swea_snail_num 1954

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d122a0cb-8924-490a-9bd0-1a996c9d7c24/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230310%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230310T154520Z&X-Amz-Expires=86400&X-Amz-Signature=ce688d9c813ee3dd663c2be416042381b71c9067e553fa67105b7224f9ead12b&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- input

```
10
1
2
3
4
5
6
7
8
9
10
```
- solve
```python
import sys

sys.stdin = open('input.txt')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())

    arr = [[0 for _ in range(N)] for _ in range(N)]

    print(f'#{test_case}')
    x = 0
    y = 0
    arr[y][x] = 1
    # 우, 하, 좌, 상 순으로 방향 전환이 계속된다.
    delta_x = [1, 0, -1, 0]
    delta_y = [0, 1, 0, -1]
    # 이동하는 방향에 따른 좌표 이동을 표현한다. 우, 하, 좌, 상
    dir_idx = 0
    count = 2

    while count <= N**2:
        # 2차원 사각형에서 총 갯수는 N의 제곱이므로 N의 제곱까지 while로 지속시켜준다.
        new_x = x + delta_x[dir_idx]
        new_y = y + delta_y[dir_idx]
        # 다음 좌표 (new_x, new_y)가 아직 사각형 안에 있는지 확인
        # 이전에 방문한 적이 없는지 확인
        if (0 <= new_x < N and 0 <= new_y < N) and arr[new_y][new_x] == 0:
            arr[new_y][new_x] = count
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
    for i in range(N):
        for j in range(N):
            print(arr[i][j], end = ' ')
        print()

```