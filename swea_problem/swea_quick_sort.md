# swea quick sort

**16754. 5205.**

- input

```
2
5
2 2 1 1 3
10
7 5 4 1 2 10 3 6 9 8
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = list(map(int, input().split()))

    def solve(board):

        if len(board) <= 1:
            return board

        ans = board[len(board) // 2]
        less = []
        more = []
        equal = []
        for num in board:
            if num < ans:
                less.append(num)
            elif num > ans:
                more.append(num)
            else:
                equal.append(num)
        return solve(less) + equal + solve(more)

    list_ans = solve(arr)
    print(f'#{test_case} {list_ans[N//2]}')

```