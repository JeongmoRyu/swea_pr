# swea_sudoku_exam 1974


![iamge](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/072d2d18-2a39-489c-a314-d939136a97d3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230317%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230317T001610Z&X-Amz-Expires=86400&X-Amz-Signature=bc5ba7fbe996139e82167c20f64a68e7b22b294d23e2d69187c26960a947932e&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- input
```
10
7 3 6 4 2 9 5 8 1
5 8 9 1 6 7 3 2 4
2 1 4 5 8 3 6 9 7
8 4 7 9 3 6 1 5 2
1 5 3 8 4 2 9 7 6
9 6 2 7 5 1 8 4 3
4 2 1 3 9 8 7 6 5
3 9 5 6 7 4 2 1 8
6 7 8 2 1 5 4 3 9
...

```

- solve

```python
import sys
sys.stdin = open("input3.txt", "r")

def sudoku(num_list):
    result = True
    for j in range(9):
        number = [0]*9
        for num in num_list[j]:
            number[int(num)-1] += 1
            if number[int(num)-1] == 2:
                result = False
                break

    return result

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////

    # 가로일 때 9개의 숫자가 존재
    # 가로의 경우를 만들어준다.
    arr = []
    for _ in range(9):
        arr.append(str(input()).split())

    # 세로일 때 9개의 숫자가 존재
    # 세로의 경우를 만들어준다.
    arr_d = []
    for i in range(9):
        arr_d.append([arr[j][i] for j in range(9)])

    # 3*3일 때 9개의 숫자가 존재
    # 사각형일때 경우를 만들어준다.
    square = []
    for a in range(3):
        for b in range(3):
            square.append([arr[a*3 + j][b*3 + i] for j in range(3) for i in range(3)])

    if sudoku(arr) and sudoku(arr_d) and sudoku(square):
        print(f'#{test_case} 1')
    else:
        print(f'#{test_case} 0')

```

- 다른 풀이

```python
import sys
sys.stdin = open("input.txt", "r")

def solve(arr):
    for lst in arr:
        if len(set(lst))!=9:
            return 0
    arr_t = list(zip(*arr))
    for lst in arr_t:
        if len(set(lst))!=9:
            return 0
    for i in (0,3,6):
        for j in (0,3,6):
            lst = arr[i][j:j+3] + arr[i+1][j:J+3] + arr[i+2][j:J+3]
            if len(set(lst))!=9:
                return 0
    return 1

T = int(input())
for test_case in range(1, T+1):
    arr = [list(map(int, input().split())) for _ in range(9)]

    ans = solve(arr)
    print(f'#{test_case} {ans}')
```