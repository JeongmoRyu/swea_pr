# swea tree arithmetic operations
1232

- solve

```python
import sys
sys.stdin = open('input.txt', 'r')

def operation(word, n, m):
    global ans
    if word == '+':
        ans = n + m
    elif word == '-':
        ans = n - m
    elif word == '*':
        ans = n * m
    else:
        ans = n / m
    return ans

def post_order(arr, node):
    global list_arr
    global arithmetic_operations
    if node != 0:
        if arr[node][1] in arithmetic_operations:
            return operation(arr[node][1], post_order(arr, arr[node][2]), post_order(arr, arr[node][3]))

        elif arr[node][1] == '0':
            return arr[node][2]

for test_case in range(1, 11):
    N = int(input())
    list_arr = [list(map(str, input().split())) for _ in range(N)]
    list_arr.insert(0, ['0', '0', '0', '0'])

    #트리를 만들어 준다.
    # tree = [[0 for _ in range(3)] for _ in range(N + 1)]

    for i in range(N+1):
        if len(list_arr[i]) != 4:
            list_arr[i].insert(1, '0')
            list_arr[i].append('0')
    # print(arr)
    arithmetic_operations = ['-', '+', '*', '/']
    for i in range(len(list_arr)):
        for j in range(2, 4):
            list_arr[i][j] = int(list_arr[i][j])
        for j in range(1):
            list_arr[i][j] = int(list_arr[i][j])
    ans = 0

    print(f'#{test_case} {round(post_order(list_arr, 1))}')
```

- input
```
너무 많다 ㅠㅠㅠ
5
1 - 2 3
2 - 4 5
3 10
4 88
5 65
7
1 / 2 3
2 - 4 5
3 - 6 7
4 261
5 61

...
```