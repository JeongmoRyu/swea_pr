# swea best score

4466

input

```python
2
3 1
100 90 80
3 2
100 90 80
```

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N, K = map(int, input().split())
    score = list(map(int, input().split()))
    # 다양한 소트를 사용할 수 있지만 sorted로 쉽게 구할 수 있다.
    list_score = sorted(score)
    ans = []
    for i in range(-1, -1-K, -1):
        ans.append(list_score[i])
    print(f'#{test_case} {sum(ans)}')

```
