# swea two numer array

1959

input

```python
#example
2
3 5
1 5 3
3 6 -7 5 4
7 6
6 0 5 5 -1 1 6
-4 1 8 7 -9 3
```

```python
import sys
sys.stdin = open('input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N, M = map(int, input().split())
    A = list(map(int, input().split()))
    B = list(map(int, input().split()))

    mx = 0

    if len(A) <= len(B):
        for i in range(len(B)-len(A)+1):
            ans = 0
            for j in range(i, i+len(A)):
                ans += A[j-i]*B[j]
            mx = max(mx, ans)

    elif len(A) > len(B):
        for i in range(len(A) - len(B) + 1):
            ans = 0
            for j in range(i, i + len(B)):
                ans += A[j] * B[j-i]
            mx = max(mx, ans)

    print(f'#{test_case} {mx}')

```