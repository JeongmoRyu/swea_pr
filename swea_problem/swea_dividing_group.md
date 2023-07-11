# swea dividing group

5248

- input

```
3
5 2
1 2 3 4
5 3
1 2 2 3 4 5
7 4
2 3 4 5 4 6 7 4
```

- solve

```python

import sys
sys.stdin = open('sample_input2.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N, M = map(int, input().split())
    arr = list(map(int, input().split()))
    visited = [0 for _ in range(N + 1)]

    for i in range(N+1):
        visited[i] = i

    # 원소가 속한 집합의 대표원소를 반환하는 함수
    def find_set(x):
        if x == visited[x]:
            return x
        return find_set(visited[x])

    def union(x, y):
        root_x = find_set(x)
        root_y = find_set(y)
        if root_x != root_y:
            visited[root_y] = root_x
        return True

    for i in range(0, M*2, 2):
        union(arr[i], arr[i+1])

    root = set()
    for i in range(1, len(visited)):
        root.add(find_set(visited[i]))
    print(f'#{test_case} {len(root)}')

```