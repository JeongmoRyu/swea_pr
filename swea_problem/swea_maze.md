# swea maze

4875

- input

```
3
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
```

```python
# import sys
# sys.stdin = open("sample_input.txt", "r")

# 방향 판별용 상수
directions = [
        (-1, 0), (0, -1), (1, 0), (0, 1)
    ]

def find_route(maze, now):
    for direction in directions:
        next_point = now[0] + direction[1], now[1] + direction[0]
        # 갈 곳이 3이면 도착이다.
        if maze[next_point[0]][next_point[1]] == 3:
            return True
        # 갈 곳이 열려있다.
        elif maze[next_point[0]][next_point[1]] == 0:
            maze[next_point[0]][next_point[1]] = 1
            # 막다른 길이면?
            if not find_route(maze, next_point):
                # 다시 돌아오자 1로 바꾸었던 걸 다시 0으로 바꾸고 이동해 온다.
                maze[next_point[0]][next_point[1]] = 0
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
    # 범위 판별이 귀찮으니 1을 넣어주자
    maze = [[1 for _ in range(N+2)]]
    for i in range(N):
        # 둘러싼 벽을 만들어서 풀어준다.
        maze_row = [1,]
        maze_row.extend(list(map(int, input())))
        maze_row.append(1)
        # if 2 in maze_row:
        #     start = (i + 1, maze_row.index(2))
        for idx, value in enumerate(maze_row):
            if value == 2:
                start = (i + 1, idx)
                break
        # maze에 maze줄 추가
        maze.append(maze_row)
        # 마지막줄 추가
    maze.append([1 for _ in range(N+2)])

    current = start

    # for row in maze:
    #     print(row)

    print(f'#{test_case} {int(find_route(maze, current))}')

```