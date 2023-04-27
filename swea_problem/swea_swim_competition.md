# swea swim competition

4192

파이썬으로 평가를 받지 못하였기 때문에 확실하지는 않습니다.

문제에서 완전탐색으로 구현하라고 하였지만 최소값을 구하는 것이게 BFS를 사용하는게 좀 더 좋아보입니다. 

DFS로 구현하였을 때 direction 방향을 어떻게 주느냐에 따라 정답이 달라져서…

주어진 output이 나올 수 있도록 방향은 바꾸어 주었습니다. 

- input

```jsx
4
6
0 1 0 0 0 0
0 1 0 1 0 1
0 1 0 1 0 0
0 0 0 1 0 0
1 1 1 1 1 1
1 1 1 1 1 1
0 0
3 5
5
0 0 0 1 0
0 1 0 0 0
0 0 1 1 0
1 0 0 0 0
0 0 1 0 0
4 0
2 4
6
0 0 1 0 0 1
0 0 1 0 0 1
0 0 0 0 0 0
0 0 0 0 1 0
1 1 1 1 1 1
1 1 1 1 1 1
0 0
3 5
5
0 0 0 0 0
0 0 0 1 0
0 0 0 1 0
1 1 1 1 0
0 0 0 0 0
4 0
2 0
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

directions = [
    (0, 1), (1, 0),  (0, -1),   (-1, 0),
]
# 방향에 따라 달라진다. 현재 output은 
# #1 14
# #2 6
# #3 8
# #4 14

def find_route(maze, now):
    global count, C, D
    for direction in directions:
        next_point = now[0] + direction[0], now[1] + direction[1]
        if next_point[0] == C+1 and next_point[1] == D+1:
            return True
        elif maze[next_point[0]][next_point[1]] == 0:
            maze[next_point[0]][next_point[1]] = 1
            count += 1
            if not find_route(maze, next_point):
                maze[next_point[0]][next_point[1]] = 0
                count -= 1
            else:
                return True
    return False

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    maze = [[1 for _ in range(N + 2)]]
    for i in range(N):
        # 둘러싼 벽을 만들어서 풀어준다.
        maze_row = [1, ]
        maze_row.extend(list(map(int, input().split())))
        maze_row.append(1)
        maze.append(maze_row)
    maze.append([1 for _ in range(N+2)])
    # print(maze)
    A, B = map(int, input().split())
    C, D = map(int, input().split())
    # visited = [[0]*(N+2) for _ in range(N+2)]

    start = (A+1, B+1)

    count = 1
    # find_route(maze, start)
    if find_route(maze, start) == False:
        print(f'#{test_case}  -1')
    else:
        print(f'#{test_case} {count}')
```