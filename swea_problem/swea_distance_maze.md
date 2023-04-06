# swea distance maze

16526
5105

- input

```python
4
5
13101
10101
10101
10101
10021
5
10031
10111
10101
10101
12001
5
00013
01110
21000
01111
00000
3
030
000
020
# 확인하기 위해서 새로운 testcase를 만들었다.
```

- 문제 발생

해결되지 않는 이유

```python
1. test_case 11개 정답 count -1씩 하면서 돌아올 때
2. test_case 6개 정답 count = 0으로 초기화하면서 돌아올 때
3. 최소값이라는 변수가 7개 정도 있을 것 같은데 list_ans를 만들어
   방향을 4방향을 바꾸어 주면 runtime error가 뜬다.
4. 3
  030
  000
  020
   이걸 넣고 풀어봤는데 1이 나오지 않고 3이 나온다...
   Dfs 형식으로 값을 구했으면 함수에서 나왔기 때문에 여러가지 길이었다면 문제가 발생하여 해결되지 않고 끝

```

```python
import sys
sys.stdin = open("sample_input (1).txt", "r")

# 방향 판별
# 상, 좌, 우, 하

dirs = [(-1, 0), (0, -1), (0, 1), (1, 0)]

def find_route(maze, now):
    for dir in dirs:
        global count
        global list_ans
        next = now[0] + dir[1], now[1] + dir[0]
        # 목적지가 3이면 도착이다.
        if maze[next[0]][next[1]] == 3:
            list_ans.append(count)
            return True
        # 가는길이 0이라면 움직일 수 있다.
        elif maze[next[0]][next[1]] == 0:
            count += 1
            maze[next[0]][next[1]] = 1
            # 막다른 길이면?
            # 더 이상 가지 못하면
            if not find_route(maze, next):
                # 다시 돌아오자 1로 바꾸었던 걸 다시 0으로 바꾸고 count 이동해 온다.
                maze[next[0]][next[1]] = 0

                count -= 1

            # 앞서 호출한 재귀함수가 성공했다.
            else:
                return True
    # 사방을 확인했지만 길이 없다면
    return False

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())

    start = None
    # 밖으로 나가지 못하도록 주변에 1이라는 벽을 만들어주자
    maze = [[1 for _ in range(N+2)]]
    for i in range(N):
        # 둘러싼 벽을 만들어서 풀어준다. 1을 만나면 부딪혀 가지 못하기 때문
        side = [1]
        side.extend(list(map(int, input())))
        side.append(1)

        # 시작점을 찾아준다.
        # 위치를 찾아주기 위해서 enumerate 함수를 사용해본다.
        for j, value in enumerate(side):
            if value == 2:
                start = (i + 1, j)
                break
        # maze에 side 추가
        maze.append(side)
        # 마지막줄 추가
    maze.append([1 for _ in range(N+2)])
    # 이렇게 하면 maze 완성

    # 움직이는 거리를 찾아주기 위해 count를 잡아준다.
    count = 0
    # print(maze)
    list_ans = []

    # find_route(maze, start)
    # print(find_route(maze, start))

    # 정상적으로 실행될시 count의 숫자구하기
    if int(find_route(maze, start)):
        print(f'#{test_case} {min(list_ans)}')

    # 목적지 도달하지 못하면 0
    else:
        print(f'#{test_case} 0')

    print(list_ans)

# 1. test_case 11개 정답 count -1씩 하면서 돌아올 때
# 2. test_case 6개 정답 count = 0으로 초기화하면서 돌아올 때
# 3. 최소값이라는 변수가 7개 정도 있을 것 같은데 list_ans를 만들어
#   방향을 4방향을 바꾸어 주면 runtime eror가 뜬다.
# 4. 3
#   030
#   000
#   020
#   이걸 넣고 풀어봤는데 1이 나오지 않고 3이 나온다...
#   Dfs 형식으로 값을 구했으면 함수에서 나왔기 때문에 여러가지 길이었다면 문제가 발생하여 해결되지 않고 끝
#

```

```python
import sys
sys.stdin = open("sample_input (1).txt", "r")

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
            return visited[x][y] - 2

        # 상하좌우 방향에 따라
        for i in range(4):
            new_x = x + di[i]
            new_y = y + dj[i]

            # 벽을 쌓아 주지 않았기 때문에 N 범위를 넣어가지 않아야 한다.
            # x범위
            if new_x < 0 or new_x >= N:
                continue
            # y범위
            if new_y < 0 or new_y >= N:
                continue

            # 상하좌우의 값들이 0, 상하좌우의 값이 3 둘 중에 하나 이고 이전 회차에 방문도 하지 않았다면
            if (maze[new_x][new_y] == 0 or maze[new_x][new_y] == 3) and visited[new_x][new_y] == 0:
                # 큐에 새로운 값을 넣어준다.
                queue.append((new_x, new_y))
                visited[new_x][new_y] = visited[x][y] + 1
                # enque 되었다는 것을 표시해준다.
    # 값이 없다면야 0을 리턴
    return False

T = int(input())

for test_case in range(1, T + 1):
    N = int(input())
    maze = [list(map(int, input())) for _ in range(N)]

    # print(arr)
    visited = [[0] * N for _ in range(N)]

    start_i = 0
    start_j = 0
    # 시작점을 찾아 본다.
    for i in range(N):
        for j in range(N):
            if maze[i][j] == 2:
                start_i = i
                start_j = j
    # False를 나오는걸 0으로 바꾸어 주기 위해 int를 넣어준다.
    print(f'#{test_case} {int(bfs(start_i, start_j))}')
```