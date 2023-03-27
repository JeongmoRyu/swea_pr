# swea_millionaire

13686

- input

```python
3
3
10 7 6
3
3 5 9
5
1 1 3 1 2

```
- solve

```python
import sys
sys.stdin = open("s_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    lst = list(map(int, input().split()))

    i = 0
    ans = 0
    while i < N:
        # 최댓값 idx 찾기
        i_mx = i
        for j in range(i+1, N):
            if lst[i_mx] < lst[j]:
                i_mx = j

        for j in range(i, i_mx):
            ans += lst[i_mx] - lst[j]

        i = i_mx + 1

    print(f'#{test_case} {ans}')

```

- 다른 풀이

```python
import sys
sys.stdin = open("s_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    lst = list(map(int, input().split()))[::-1]
    ans = mx = 0
    for n in lst:
        if mx > n:
            ans += mx -n
        else:
            mx = n
    print(f'#{test_case} {ans}')
```

- output

```python
#1 0
#2 10
#3 5
```