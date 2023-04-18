# swea seok's_talk_downrow
5356
- input

```python
2
ABCDE
abcde
01234
FGHIJ
fghij
AABCDD
afzz
09121
a8EWg6
P5h3kx
```

- solve
```python
import sys
sys.stdin = open('sample_input1.txt', 'r')

T = int(input())

for test_case in range(1, T+1):

    board = [list(input()) for _ in range(5)]
    len_board = []
    for i in range(5):
        len_board.append(len(board[i]))
    mx = max(len_board)

    x = 0
    while x != 5:
        if mx == len(board[x]):
            x += 1
        else:
            board[x].append('-')

    down_board = list(zip(*board))

    answer = []
    # for i in range(mx):
    #     if '-' in down_board[i]:
    #         down_board[i].del('-')
    # print(down_board)

    for i in range(mx):
        for j in range(5):
            if down_board[i][j] != '-':
                answer.append(down_board[i][j])

    print(f'#{test_case}', ''.join(answer))

```