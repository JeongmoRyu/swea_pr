# swea_simple_Alzip1
1946

![image](https://www.notion.so/swea_simple_Alzip-c9eee0e4bf1e46e387c3046a8c638f7a?pvs=4#65cb5fa5b44e4953b29c94684f461b0a)
input

```python

1
3
A 10
B 7
C 5
```

```python
import sys
sys.stdin = open("input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())

    arr = ''

    for _ in range(N):
        Alp, num = map(str, input().split())
        arr += Alp*int(num)

    print(f'#{test_case}')
    i = 0
    while i <= len(arr):
        print(arr[i + 0 : i+10])
        i += 10

```