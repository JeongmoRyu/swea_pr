# swea_electric_bus  4831, 16127

input 

```
3
3 10 5
1 3 5 7 9
3 10 5
1 3 7 8 9
5 20 5
4 7 9 14 17
```

```python
import sys
sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    
    K, N, M = map(int, input().split())
    charge = list(map(int, input().split()))

    # K = 한번에 갈 수 있는 거리
    # N = 총 정거정 갯수
    # M = 충전기 갯수
    here = 0
    count = 0

    while here < N:
        for mov in range(K, 0, -1):
            # 역순으로 제일 멀리부터 가보는 식으로 이동을 수행한다.
            if (here + mov) >= N:
                here = N
                break
            elif (here + mov) in charge:
                here = here + mov
                count += 1
                break
        else:
            count = 0
            break
    print(f'#{test_case} {count}')
```


