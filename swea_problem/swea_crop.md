# swea crop

2805

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/420add26-9b2b-46ce-8025-47f8e7f5eb2c/Untitled.png)

sample_input

```python
1
5
14054
44250
02032
51204
52212
```

```python
T = int(input())

for test_case in range(1, 1+ T):
    N = int(input())
    arr = [list(input()) for _ in range(N)]

    list_ans = 0
    i = 0
    j = 0
    if N == 1:
        list_ans = arr[0][0]

    while i != N and N != 1:
        if i < N//2:
            for x in range(N//2 - j, N//2 + j + 1):
                list_ans += int(arr[i][x])
            i += 1
            j += 1
        elif i == N//2:
            for x in range(N//2 - j, N//2 + j + 1):
                list_ans += int(arr[i][x])
            i += 1
            j -= 1
        else:
            for x in range(N//2 - j, N//2 + j + 1):
                list_ans += int(arr[i][x])
            i += 1
            j -= 1

    print(f'#{test_case} {list_ans}')
```