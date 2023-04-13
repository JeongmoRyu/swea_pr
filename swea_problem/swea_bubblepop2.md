# swea bubble pop2

16268

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2daa8979-4c86-4f7d-94fc-31ebb81234d7/Untitled.png)

- input

```python
3
3 5
2 1 1 2 2 
2 2 1 2 2 
2 2 1 1 2 
5 5
3 4 1 2 3 
3 4 1 3 2 
2 3 2 4 1 
1 4 4 1 3 
2 2 3 4 4 
5 8
1 3 4 4 4 4 3 3 
4 1 2 4 3 1 4 4 
4 1 4 4 1 4 2 1 
3 2 4 2 1 1 2 1 
4 4 1 4 4 2 2 2
```
- solve

```python
import sys
sys.stdin = open('input1.txt', 'r')

T = int(input())

for test_case in range(1, T+1):
    N, M = map(int, input().split())

    bubble = [[0]*(M+2)]
    for _ in range(N):
        bubble.append([0] + list(map(int, input().split())) + [0])
    bubble.append([0]*(M+2))

    dir_x = [0, -1, 1, 0, 0]
    dir_y = [0, 0, 0, 1, -1]
    list_num = []
    num = []
    for i in range(1, N):
        for j in range(1, M):
            for k in range(5):
                new_x = i + dir_x[k]
                new_y = j + dir_y[k]
                num.append(bubble[new_x][new_y])

            list_num.append(sum(num))
            num = []
    print(f'#{test_case} {max(list_num)}')
```