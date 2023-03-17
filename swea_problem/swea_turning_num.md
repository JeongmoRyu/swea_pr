# swea turning num 1961

- input
```
10
3
1 2 3
4 5 6
7 8 9
6
6 9 4 7 0 5
8 9 9 2 6 5
6 8 5 4 9 8
2 2 7 7 8 4
7 5 1 9 7 9
8 9 3 9 7 6
…
```
- solve

```python
import sys
sys.stdin = open("input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    arr = [input().split() for _ in range(N)]

    # 90도 회전
    # 나머지들을 90도 회전을 여러번 시켜도 되지만 연습을 해보자
    # arr1[i][j] = arr[N-1-j][i]
    # 180도 회전
    # arr2[i][j] = arr[N-1-i][N-1-j]
    # 270도 회전
    # arr3[i][j]= arr[j][N-1-i]

    # 90도
    arr1 = [[0] * N for _ in range(N)]
    # 180도
    arr2 = [[0] * N for _ in range(N)]
    # 270도
    arr3 = [[0] * N for _ in range(N)]

    for i in range(N):
        for j in range(N):
            arr1[i][j] = arr[N-1-j][i]
            arr2[i][j] = arr[N-1-i][N-1-j]
            arr3[i][j] = arr[j][N-1-i]
    print(f'#{test_case}')
    for a, b, c in zip(arr1, arr2, arr3):
        print(f'{"".join(a)} {"".join(b)} {"".join(c)}')

```