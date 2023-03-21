# swea graph dir 4871

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7c9c6e8c-abac-4959-8a67-ef6e6e188309/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230321%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230321T001254Z&X-Amz-Expires=86400&X-Amz-Signature=1a51b9862778305c43ae5778a9e13e2b3c7c426ae255a976667a2243e81b5fe3&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

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
2 5
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
sys.stdin = open('../sample_input.txt', 'r')

def depth_first_search(ver):
    # 함수 호출되면 거기 방문한 것
    visited[ver] = 1
    # 작은 숫자부터 세기
    for next in range(1, V + 1):
        # 인접하고 미방문이면
        if adjM[ver][next] == 1 and visited[next] == 0:
            # 다음 함수 호출
            depth_first_search(next)

T = int(input())
for test_case in range(1, T + 1):
    V, E = map(int, input().split())

    visited = [0 for _ in range(V + 1)]

    adjM = [[0] * (V + 1) for _ in range(V + 1)]

    for i in range(E):
        s, g = map(int, input().split())
        adjM[s][g] = 1

    start, end = map(int, input().split())

    depth_first_search(start)

    ans = 0
    if visited[end] == 1:
        ans = 1

    print(f'#{test_case} {ans}')
```