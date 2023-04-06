# swea maze2
1227

```python
input이 무지하게 많다.
```

input이 무지하게 많기 때문에

maze1과 같이 문제를 풀면 runtime error가 뜬다.

```python
import sys
sys.stdin = open('input.txt', 'r')

# 방향 판별
# 상, 좌, 우, 하

dirs = [(-1, 0), (0, -1), (0, 1), (1, 0)]

def find_route(maze, now):
    for dir in dirs:
        next = now[0] + dir[1], now[1] + dir[0]
        # 목적지가 3이면 도착이다.
        if maze[next[0]][next[1]] == '3':
            return True
        # 가는길이 0이라면 움직일 수 있다.
        elif maze[next[0]][next[1]] == '0':
            maze[next[0]][next[1]] = '1'
            # 막다른 길이면?
            # 더 이상 가지 못하면
            if not find_route(maze, next):
                # 다시 돌아오자 1로 바꾸었던 걸 다시 0으로 바꾸고 count 이동해 온다.
                maze[next[0]][next[1]] = '0'

            # 앞서 호출한 재귀함수가 성공했다.
            else:
                return True
    # 사방을 확인했지만 길이 없다면
    return False

# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.

for test_case in range(1, 11):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())

    start = None
    # 밖으로 나가지 못하도록 주변에 1이라는 벽을 만들어주자
    maze = [list(input()) for _ in range(16)]

    # 시작점을 찾아준다.
    for i in range(16):
        for j in range(16):
            if maze[i][j] == '2':
                start = (i, j)
                break
    # print(start)
    # 시작점이 다 1,1이다.
    # find_route(maze, start)
    # print(find_route(maze, start))

    # 목적지 도달하면 1
    if int(find_route(maze, start)):
        print(f'#{test_case} 1')
    # 목적지 도달하지 못하면 0
    else:
        print(f'#{test_case} 0')

```

그렇기에 다른 방법으로 풀어보자

bfs방식으로 풀기

해결!!

```python
import sys
sys.stdin = open('input.txt', 'r')

# 갈 수 있는 방향
# 좌, 상, 우, 하
di = [0, -1, 0, 1]
dj = [-1, 0, 1, 0]

# bfs 방식으로 풀어보기
# 찾은 시작점 start_i, start_j 을 넣어준다.
def bfs(start_i, start_j):
    # 큐 생성하고 첫 번째 요소 넣어준다.
    queue = [(start_i, start_j)]
    # 그리고 visited 함수에 시작점을 넣어준다.
    visited[start_i][start_j] = 1

    while queue:
        # q가 비어있지 않으면
        # 첫 번째 요소 pop
        x, y = queue.pop(0)

        # while 목적지인 3을 찾았을 때
        if maze[x][y] == 3:
            # 2를 뺀 이유는 시작과 도착때도 visited에 1씩 추가가 되었기 때문에
            return True

        # 상하좌우 방향에 따라
        for i in range(4):
            new_x = x + di[i]
            new_y = y + dj[i]

            # 벽을 쌓아 주지 않았기 때문에 N 범위를 넣어가지 않아야 한다.
            # x범위
            if new_x < 0 or new_x >= 100:
                continue
            # y범위
            if new_y < 0 or new_y >= 100:
                continue

            # 상하좌우의 값들이 0, 상하좌우의 값이 3 둘 중에 하나 이고 이전 회차에 방문도 하지 않았다면
            if (maze[new_x][new_y] == 0 or maze[new_x][new_y] == 3) and visited[new_x][new_y] == 0:
                # 큐에 새로운 값을 넣어준다.
                queue.append((new_x, new_y))
                visited[new_x][new_y] = visited[x][y] + 1
                # enque 되었다는 것을 표시해준다.
    # 값이 없다면야 0을 리턴
    return False

# T = int(input())

for test_case in range(1, 11):
    N = int(input())

    maze = [list(map(int, input())) for _ in range(100)]
    # print(maze)
    # print(arr)
    visited = [[0] * 100 for _ in range(100)]
    start_i = 0
    start_j = 0

    for i in range(100):
        for j in range(100):
            if maze[i][j] == 2:
                start_i = i
                start_j = j

    # 시작점을 찾아 본다.
    # 찾아보니 시작점이 다 1, 1이기에 start_i, start_j를 1, 1로 잡아도된다.

    # False를 나오는걸 0으로 바꾸어 주기 위해 int를 넣어준다.
    print(f'#{test_case} {int(bfs(start_i, start_j))}')
```