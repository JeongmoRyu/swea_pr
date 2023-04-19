# swea killing fly3

12712

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b825ea6c-7d91-47ab-9a02-d9260d3b0bb5/Untitled.png)

input

```jsx
2
5 2
1 3 3 6 7
8 13 9 12 8
4 16 11 12 6
2 4 1 23 2
9 13 4 7 3
6 3
29 21 26 9 5 8
21 19 8 0 21 19
9 24 2 11 4 24
19 29 1 0 21 19
10 29 6 18 4 3
29 11 15 3 3 29
```

```python
import sys
sys.stdin = open('s_in1.txt', 'r')

T = int(input())

for test_case in range(1, T + 1):
    N, M = map(int, input().split())

    board = [[0]*(N+2*M) for _ in range(M)]
    for _ in range(N):
        board.append([0]*M + list(map(int, input().split())) + [0]*M)
    board.extend([[0]*(N+2*M) for _ in range(M)])

    # 상하좌우 오른쪽대각선위 오른쪽대각선아래 왼쪽대각선위 왼쪽 대각선 아래
    dir_x = [0, -1, 1, 0, 0, -1, 1, -1, 1]
    dir_y = [0, 0, 0, -1, 1, 1, 1, -1, -1]

    # 플러스 모양 리스트
    list_ans_plus = []
    # x 모양 리스트
    list_ans_x = []
    # 파리 잡은 수들을 더한 값들을 리스트한 것
    list_ans = []
    for i in range(M, M+N+1):
        for j in range(M, M+N+1):
            list_ans_plus.append(board[i][j])
            list_ans_x.append(board[i][j])
            for a in range(1, 5):
                for b in range(1, M):
                    list_ans_plus.append(board[i + b * dir_x[a]][j + b * dir_y[a]])

            list_ans.append(sum(list_ans_plus))
            list_ans_plus = []

            for c in range(5, 9):
                for d in range(1, M):
                    list_ans_x.append(board[i + d * dir_x[c]][j + d * dir_y[c]])

            list_ans.append(sum(list_ans_x))
            list_ans_x = []

    print(f'#{test_case} {max(list_ans)}')

```