# swea bubblepop

9490

터진 풍선의 꽃가루 갯수만큼 상하좌우로 터진다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c2d2714c-8742-4306-8ffe-580ab0db6e00/Untitled.png)

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

    arr = [list(map(int, input().split())) for _ in range(N)]

    dir_x = [-1, 1, 0, 0]
    dir_y = [0, 0, -1, 1]
    mx = 0
    for i in range(N):
        for j in range(M):

            list_ans = []
            list_ans.append(arr[i][j])
            for k in range(4):
                num = 1
                new_x = 0
                new_y = 0
                while num <= arr[i][j]:
                    new_x = i + num*dir_x[k]
                    new_y = j + num*dir_y[k]
                    if 0 <= new_x < N and 0 <= new_y < M:
                        list_ans.append(arr[new_x][new_y])
                    num += 1
            # print(list_ans)
            mx = max(mx, sum(list_ans))

    print(f'#{test_case} {mx}')

```