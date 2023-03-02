## swea_ss_buslane 6485

- input

```
1 //테스트 케이스 개수
2 //첫 번째 테스트 케이스, N=2
1 3 // A1 = 1, B1 = 3
2 5 // A2 = 2, B2 = 5
5 // P = 5
1 // 이하 C1 = 1, C2 = 2, C3 = 3, C4 = 4, C5 = 5
2
3
4
5	
 
```

- 풀이
```python
import sys
sys.stdin = open("../s_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    # N번 반복하면서 노선입력
    # A1, B1 = list(map(int, input().split()))
    # A2, B2 = list(map(int, input().split()))

    cnts = [0] * 5001
    # 5000개 count 수
    for _ in range(N):
        S, E = map(int, input().split())
        for i in range(S, E+1):
            cnts[i] += 1

    P = int(input())
    alist = []

    for _ in range(P):
        p = int(input())
        alist.append(cnts[p])

    print(f'#{test_case}', *alist)
```