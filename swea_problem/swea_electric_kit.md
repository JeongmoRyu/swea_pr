# swea electric kit 5189

- input

```html
3
3
0 18 34
48 0 55
18 7 0
4
0 83 65 97
82 0 78 6
19 19 0 82
6 34 94 0
5
0 9 26 85 42
14 0 84 31 27
58 88 0 16 46
83 61 94 0 17
40 71 24 38 0
```

- solve

```python
# 5189 electirc kit

import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]

    def solve(start, count):
        global list_ans
        global stack
        if start < N-1:
            for i in range(1, N):
                if visited[i] != 0:
                    continue
                visited[i] = 1
                stack.append(i)
                solve(start + 1, count + arr[stack[start]][stack[start + 1]])
                visited[i] = 0
                stack.pop()
        else:
            count += arr[stack[-1]][0]
            list_ans.append(count)
            return

    visited = [0]*N
    stack = [0]
    list_ans = []
    solve(0, 0)
    # print(list_ans)
    print(f'#{test_case} {min(list_ans)}')

```