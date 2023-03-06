
# swea_fly_in_train 6019

- input

```
1
250 10 15 20
```

- solve


```python
import sys
sys.stdin = open('input.txt', 'r')
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    D, A, B, F = map(int, input().split())
    dis_sum = 0
    idx = 0
 
    while D >= 10 ** (-6):
        if idx % 2 == 0:
            dis = (D * B * F) / (F * (B + F))
            dis_sum += dis
 
        else:
            dis = (D * A * F) / (F * (A + F))
            dis_sum += dis
 
        t = dis / F
        D -= (A + B) * t
 
    print(f'#{test_case} {dis_sum}')

```

