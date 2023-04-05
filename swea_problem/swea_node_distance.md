# swea node distance
16527


- input

```python
3
6 5
1 4
1 3
2 3
2 5
4 6
1 6 
7 4
1 6
2 3
2 6
3 5
1 5 
9 9
2 6
4 7
5 7
1 5
2 9
3 9
4 8
5 3
7 8
1 9
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())

def bfs(v, N):
    # v 시작점, N 마지막지점
    global visited
    global list_ans
    queue = [v]
    visited[v] = 1
    while queue:
        # q가 비어있지 않으면
        t = queue.pop(0)
        # print(t)
        current_distance = visited[t]
        list_ans.append(t)
        # print(t, end = '-')
        for v in adjL[t]:
            # t에 인접하고 방문한적 없는 v
            if visited[v] == 0:
                queue.append(v)
                # v 인큐
                visited[v] = visited[t] + 1
                # v 인큐되었음을 표시
                # 거리 정보 추가
                visited[v] = current_distance + 1

for test_case in range(1, T + 1):
    V, E = map(int, input().split())
    adjL = [[] for _ in range(V + 1)]

    for _ in range(E):
        s, g = map(int, input().split())
        adjL[s].append(g)
        adjL[g].append(s)
        # 방향성을 가지고 있기에 둘다 입력해준다.
    start, end = map(int, input().split())
    visited = [0] * (V + 1)
    list_ans = []
    # bfs 실행
    bfs(start, end)

    # print(list_ans)
    if start and end not in list_ans:
        print(f'#{test_case} 0')
    else:
        print(f'#{test_case} {visited[end] - visited[start]}')

    # print(test_case)
    # print(visited)

```