# swea partial num 4837

input

```python
3
3 6
5 15
5 10
```

```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N, K = list(map(int, input().split()))
    A = [a for a in range(1, 13)]
    count = 0
    for a in range(1<< 12):
        subset = []

        sum = 0
        for b in range(12):
            if a & (1 << b):
                subset.append(A[b])

                sum += A[b]
        if len(subset) == N and sum == K:
            count += 1

    print(f'#{test_case} {count}')
```