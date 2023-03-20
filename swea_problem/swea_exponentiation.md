# swea_exponentiation(거듭제곱) 1217


```python
input
1
9 8
2
2 8
3
6 5
4
10 7
5
6 7
6
7 2
7
9 8
8
3 2
9
4 8
10
8 6
```

```python
import sys
sys.stdin = open('input.txt', 'r')

T = 10
for test_case in range(1, T+1):
    whatever = int(input())
    N, M = map(int, input().split())
    ans = 1
    while M > 0:
        if M > 0:
            ans = ans * N
            M = M - 1

    print(f'#{test_case} {ans}')
```