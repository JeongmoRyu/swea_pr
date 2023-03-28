# swea_othello_game

4615

- input

```python
1
4 12 
1 2 1
1 1 2
4 3 1
4 4 2
2 1 1
4 2 2
3 4 1
1 3 2
2 4 1
1 4 2
4 1 2
3 1 2
```

- solve

```python
import sys
sys.stdin = open("input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N, M = map(int, input().split())
    # arr 상하좌우  0 패딩으로 둘러쌈
    arr = [[0]*(N+2) for _ in range(N+2)]
    m = N//2
    # 초기 위치
    arr[m][m] = arr[m+1][m+1] = 2
    arr[m+1][m] = arr[m][m+1] = 1

    # 흑돌 백돌 입력 바아서 처리
    for _ in range(M):
        si, sj, d = map(int, input().split())
        arr[si][sj] = d

        for di, dj in ((-1, -1), (-1, 0), (-1, 1), (0, -1), (0, 1), (1, -1), (1, 0), (1, 1)):
            # 해당방향으로 뻗어나가면서 처리
            tlst = []
            for mul in range(1, N):
                ni, nj = si+di*mul, sj+dj*mul
                if arr[ni][nj] == 0:
                    # 빈칸 범위 밖
                    break
                # 다른 돌인 경우 뒤집기 후보에 추가
                elif arr[ni][nj] != d:
                    tlst.append((ni, nj))
                # 같은돌 후보들을 뒤집는다. 그리고 종료
                else:
                    while tlst:
                        ti, tj = tlst.pop()
                        arr[ti][tj]= d
                    break

    bcnt = wcnt = 0
    for lst in arr:
        bcnt += lst.count(1)
        wcnt += lst.count(2)

    print(f'#{test_case} {bcnt} {wcnt}')
```