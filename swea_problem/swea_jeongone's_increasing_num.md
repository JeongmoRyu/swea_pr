# swea jeonggone's increasing num
6190
```jsx
1
4
2 4 7 10
```

```python


import sys
sys.stdin = open("s_input.txt", "r")

def check(num):
    for k in range(len(num)-1):
        if num[k] > num[k+1]:
            return False
    return True

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = list(map(int, input().split()))

    ans = -1

    for i in range(N):
        for j in range(i+1, N):
            number = str(arr[i]*arr[j])

            if ans < int(number) and check(number):
                ans = int(number)

    print(f'#{test_case} {ans}')
```