# swea_flying_aircraft_landing2
10760

- input
```
3
3 5
2 3 1 8 9 
7 6 2 2 6 
5 7 3 8 7 
5 5
5 2 3 5 2 
5 5 8 4 5 
3 6 8 5 2 
8 2 3 3 3 
5 1 5 4 5 
5 8
8 7 2 5 2 4 3 1 
7 4 2 3 9 3 5 1 
5 7 6 2 2 7 9 6 
9 8 7 6 2 1 9 4 
1 9 4 9 2 3 5 2 
10 5
6 1 2 3 3 
5 2 4 6 9 
2 3 8 4 5 
4 9 7 4 3 
2 8 5 9 7 
6 1 8 7 4 
1 4 5 8 6 
5 6 2 8 5 
4 2 9 8 2 
1 9 9 6 9 
```

- solve
```python
# 이곳에 코드 작성
import sys
sys.stdin = open('input2.txt', 'r')

T = int(input())

for test_case in range(1, T + 1):
    N, M = map(int, input().split())

    board = []
    board += [[9]*(M+2)]

    arr = [[9] + list(map(int, input().split())) + [9] for _ in range(N)]
    board.extend(arr)
    board += [[9]*(M+2)]
    # 전체를 9로 둘러싼 벽을 만들어 준다. 가장자리들도 확인해보아야하기 때문에
    # [[9, 9, 9, 9, 9], [2, 3, 1, 8, 9], [7, 6, 2, 2, 6], [5, 7, 3, 8, 7], [9, 9, 9, 9, 9]]

    # 갈 수 있는 방향 8가지를 만들어 준다.
    dir_x = [-1, -1, -1, 0, 0, 1, 1, 1]
    dir_y = [-1, 0, 1, -1, 1, -1, 0, 1]
    # print(board)
    ans = 0
    # 정답이 되는 ans를 만들어준다.
    # 밖은 9로 된 벽이기에 1부터 시작하여 끝 점도 하나 제외해서 결과를 도출한다.
    for i in range(1, N+1):
        for j in range(1, M+1):
            # 검사할 지점들을 구하기 위한 i, j
            # 가장자리들이 들어갈 list를 만들어준다.
            side = []
            for k in range(8):
                dx = dir_x[k]
                dy = dir_y[k]
                side.append(board[i + dx][j + dy])
                # 검사할 지점들 옆의 8자리 side를 다 리스트에 넣어준다.
                cnt = 0
                # 사이드들 점에서 검사할 지점들보다 작은 점들이 있을 떄 count를 올린다.
                for l in range(len(side)):
                    if board[i][j] > side[l]:
                        cnt += 1
            # 나갈 수 있는 방향이 4개 이상이라면 정답을 올려준다.
            if cnt >= 4:
                ans += 1
            side = []
            cnt = 0

    print(f'#{test_case} {ans}')
```