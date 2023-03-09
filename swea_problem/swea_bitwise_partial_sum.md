# swea_bitwise_partialsum 16261

- input

```python
3
19 6 16 19 15 16 8 13 16 10

-20 -6 -13 3 -19 -9 19 -3 9 4

7 7 19 1 -18 5 -9 -11 19 18
```

- solve

```python
import sys
sys.stdin = open("in2.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    arr = list(map(int, input().split()))
    N = len(arr)
    # 몇개의 원소를 가지는지 찾는다.
    # bit = [0]*N 밑의 내용과 거의 동일하다.
    bit = [0 for _ in range(N)]
    for i in range(1, 1 << N):
        # i 가 0에서 1023까지 반복하게 된다.
        subset_sum = 0
        for j in range(N):
            if i & (1 << j):
                subset_sum += arr[j]
                # 부분집합 구하기

        if subset_sum == 0:
            print(f'#{test_case} 1')
            break
    else:
        print(f'#{test_case} 0')

```