
# swea_growing_carrot 9367

- input
```
3
5
1 2 3 4 5
5
4 5 1 2 3
5
5 4 3 2 1
```

- solve

```python
import sys
sys.stdin = open("input1.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    carrot = list(map(int, input().split()))
    count = 1
    X = []
    for a in range(1, N):

        if carrot[a-1] < carrot[a]:
            count += 1
            X.append(count)
        else:
            count = 1
            X.append(count)
    max_num = max(X)
    print(f'#{test_case} {max_num}')
```