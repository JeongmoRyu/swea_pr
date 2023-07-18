# swea short distance

5251

- input

```
3
2 3
0 1 1
0 2 6
1 2 1
4 7
0 1 9
0 2 3
0 3 7
1 4 2
2 3 8
2 4 1
3 4 8
4 6
0 1 10
0 2 7
1 4 2
2 3 10
2 4 3
3 4 10
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

def dfs(num, sm):
    global mn
    if sm > mn:
        return
    if num == N:
        mn = min(sm, mn)
        return
    for i in range(len(distance[num])):
        if visited[distance[num][i][0]] == 1:
            continue
        visited[distance[num][i][0]] = 1
        dfs(distance[num][i][0], sm + distance[num][i][1])
        visited[distance[num][i][0]] = 0

T = int(input())
for test_case in range(1, T+1):
    N, E = map(int, input().split())
    distance = [[] for _ in range(N+1)]
    for i in range(E):
        s, e, w = map(int, input().split())
        distance[s].append([e, w])
    # print(N, E)
    visited = [0]*(N+1)

    mn = 1000*1000000
    visited[0] = 1
    dfs(0,0)
    print(f'#{test_case} {mn}')

```