# swea omok

11315

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T + 1):  
    N = int(input())
    arr = [list(map(str, input())) for _ in range(N)]
    # print(arr1)
    # 가로
    count = 0
        
    dir_x = [1, 0, 1, -1]
    dir_y = [0, 1, 1, 1]
    
    new_i = 0
    new_j = 0
    ans = 'NO'
    for i in range(N):
        for j in range(N):
            if arr[i][j] == 'o':
                for dir in range(4):
                    count = 1
                    new_i = i + dir_x[dir]
                    new_j = j + dir_y[dir]
                    while 0<=new_i<N and 0<=new_j<N and arr[new_i][new_j] == 'o':
                        count += 1
                        new_i = new_i+dir_x[dir]
                        new_j = new_j+dir_y[dir]
    
                    if count >= 5:
                        ans = 'YES'

  
    print(f'#{test_case} {ans}')
```

input

```jsx
4
5
....o
...o.
..o..
.o...
o....
5
...o.
ooooo
...o.
...o.
.....
5
.o.oo
oo.oo
.oo..
.o...
.o...
5
.o.o.
o.o.o
.o.o.
o.o.o
.o.o.

```