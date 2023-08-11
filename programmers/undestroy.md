# undestroy

답은 다 맞았지만 효율성 테스트가 다 틀렸다.

```python
def solution(board, skill):
    for i in range(len(skill)):
        if skill[i][0] == 1:
            for j in range(skill[i][1], skill[i][3] + 1):
                for k in range(skill[i][2], skill[i][4] + 1):
                    board[j][k] -= skill[i][5]
        else:
            for j in range(skill[i][1], skill[i][3] + 1):
                for k in range(skill[i][2], skill[i][4] + 1):
                    board[j][k] += skill[i][5]
    print(board)
    answer = 0
    for i in range(len(board)):
        for j in range(len(board[0])):
            if board[i][j] > 0:
                answer += 1

    return answer
```

누적합을 구해서 복잡도를 감소시켜야한다고 했다. 인터넷 참조

```python
def solution(board, skill):
    answer = 0 
    h = len(board)
    w = len(board[0])
    temp = [[0] * w for _ in range(h)] 
    for [t, r1, c1, r2, c2, d] in skill:
        if t == 1: 
            temp[r1][c1] -= d
            if r2+1 < h and c2+1 < w:
                temp[r2+1][c2+1] -= d
            if r2+1 < h:
                temp[r2+1][c1] += d
            if c2+1 < w:
                temp[r1][c2+1] += d             
        else:
            temp[r1][c1] += d
            if r2+1 < h and c2+1 < w:
                temp[r2+1][c2+1] += d
            if r2+1 < h:
                temp[r2+1][c1] -= d
            if c2+1 < w:
                temp[r1][c2+1] -= d
        
    for i in range(h):
        for j in range(1, w):
            temp[i][j] += temp[i][j-1]
            
    for j in range(w):
        for i in range(1, h):
            temp[i][j] += temp[i-1][j]
    
    for i in range(h):
        for j in range(w):
            board[i][j] += temp[i][j]
            if board[i][j] > 0:
                answer += 1
            
    return answer
```