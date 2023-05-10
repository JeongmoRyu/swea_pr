# swea sum sequence

2817 **16898**

- input

```
1
4 3
1 2 1 2

```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N, K = map(int, input().split())
    arr = list(map(int, input().split()))

    list_ans = []
    def solve(i, k):
        if i == k:
            num = 0
            for j in range(k):
                if bit[j] == 1:
                    num += arr[j]
            list_ans.append(num)

        else:
            bit[i] = 1
            solve(i + 1, k)
            bit[i] = 0
            solve(i + 1, k)

    N = len(arr)
    bit = [0] * N
    solve(0, N)
    ans = 0
    for i in range(len(list_ans)):
        if list_ans[i] == K:
            ans += 1

    print(f'#{test_case} {ans}')
```