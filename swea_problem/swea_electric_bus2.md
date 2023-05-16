# swea electric bus 2

5208

- input

```
3
5 2 3 1 1
10 2 1 3 2 2 5 4 2 1
10 1 1 2 1 2 2 1 2 1
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    arr = list(map(int, input().split()))
    N = arr[0]
    count = 0
    print(arr)
    num = 1
    max_num = num + arr[num]

    while max_num < N:
        for i in range(num + 1, max_num + 1):
            if i + arr[i] > max_num:
                max_num = i + arr[i]
                num = i
        count += 1
    print(f'#{test_case} {count}')

```