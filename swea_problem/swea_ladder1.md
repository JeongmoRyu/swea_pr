# swea_ladder 1 1210



![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b19cee14-78d9-4b18-be75-80c715ce7883/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230312%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230312T010412Z&X-Amz-Expires=86400&X-Amz-Signature=276b447975cf2d489637a55fe0100ca0db29484e1e1ce755eddb83d8504beba2&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

```python

import sys
sys.stdin = open("input.txt", "r")

# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, 11):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    arr = [[0] + list(map(int, input().split())) + [0] for _ in range(100)]
    # arr.append(map(int, input().split()))

    # 문제에 대한 고찰
    # 시작점을 찾는 것이기에 정답 반대에서 시작함을 생각해본다.
    # 이를 통해 종착점에서 반대로 위로 올라간다는 방향성을 가진다.
    # 시작점이 2인점을 찾는다.
    # 1을 따라 올라간다.
    # 위로 올라가다가 오른쪽이나 왼쪽을 만나면 방향을 바꾼다.
    # 올라가다가 더 못올라가게 된다면 그 때의 x 값을 찾아준다.

    count = 0
    dir_idx = 0
    # 0 : 위, 1 : 오, 2 :왼
    delta_x = [-1, 0, 0]
    delta_y = [0, 1, -1]
    # 위 오 왼

    # 시작점이 2인점을 찾는다.
    # 1을 따라 위로 올라가다가
    # 오른쪽 혹은 왼쪽에 1이 존재하면 그 방향으로 방향 전환을 한다.
    # 오른쪽 왼쪽으로 가던 방향이 0을 만나면 다시
    # 위 방향의 1을 따라 올라간다.
    # 다음 좌표가 아직 사각형 안에 있는지 확인
    x = 99
    fin = 0
    for a in range(102):
        if arr[99][a] == 2:
            fin = a
    # 시작점이 2인 점을 찾았다.
    while True:
        # 위로 올라갈 수 없는 경우
        if x == 0:

            break
            # 왼쪽에 1이 존재할 경우
        if arr[x][fin-1]:
            dir_idx = 2
            while True:
                x += delta_x[dir_idx]
                fin += delta_y[dir_idx]
                if arr[x][fin-1] == 0:
                    # 왼쪽으로 가는 방향에서 1이 끝날 경우
                    break
        elif arr[x][fin+1]:
            # 오론 쪽에 1이 존재할 경우
            dir_idx = 1
            while True:
                x += delta_x[dir_idx]
                fin += delta_y[dir_idx]
                if arr[x][fin + 1] == 0:
                    # 오른 쪽으로 가는 방향에서 1이 끝날 경우
                    break
        dir_idx = 0
        x += delta_x[dir_idx]
        fin += delta_y[dir_idx]

        # 1을 따라 위로 올라가다가
        # 위 방향의 1을 따라 올라간다.
        # 다음 좌표가 아직 사각형 안에 있는지 확인
    print(f'#{N} {fin-1}')

    # ///////////////////////////////////////////////////////////////////////////////////

```

다른 풀이

```python
import sys
sys.stdin = open('input.txt')

for _ in range(1, 11):
    test_case = int(input())
    ladder = []
    for _ in range(100):
        ladder.append(list(map(int, input().split())))

    for i in range(100):
        # 0 - 99 사이에
        if ladder[99][i] == 2:
            # 도착지를 찾아준다.
            y = 99
            x = i

    # 좌 우 상
    dx = [-1, 1, 0]
    dy = [0, 0, -1]
    # 꼭대기에 도착할 때까지 실행한다.
    while y != 0:
        for dir_idx in range(3):
            new_x = x + dx[dir_idx]
            new_y = y + dy[dir_idx]
		# 사각형 안에 있는지에 대한 조건을 더한다.
            if (0 <= new_y < 100 and 0 <= new_x < 100) and ladder[new_y][new_x] == 1:
		# 새로운 x, y에 따라 1이 있으면 이동한다.
		# 이전 좌표에 가지 않아야 한다. 안 그렇게 설정하면 결국 진동하다가 위로 올라가게된다.

                ladder[y][x] = 0
		# 있었던 좌표를 0으로 변화시켜준다.
                x = new_x
                y = new_y

    print(f'#{test_case} {x}')
```
