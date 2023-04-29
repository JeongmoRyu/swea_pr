# swea min sum

5188
- input

```python
3
3
1 2 3
2 3 4
3 4 5
4
2 4 1 3
1 1 7 1
9 1 7 10
5 7 2 4
5
6 7 1 10 2
10 2 7 5 9
9 3 2 9 6
1 6 8 2 9
8 3 8 2 1

```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]

    dir_x = [0, 1]
    dir_y = [1, 0]

    ans = 10*N**2
    start = (0, 0)
    end = (N, N)
    def solve(new, answer):
        global ans
        if answer > ans:
            return
        if new[0] >= N or new[1] >= N:
            return
        elif new[0] == N - 1 and new[1] == N - 1:
            answer += arr[new[0]][new[1]]
            if ans > answer:
                ans = answer
            return
        else:
            answer += arr[new[0]][new[1]]
            new_point_x = (new[0]+1, new[1])
            solve(new_point_x, answer)
            new_point_y = (new[0], new[1]+1)
            solve(new_point_y, answer)

    solve(start, 0)

    print(f'#{test_case} {ans}')
```