# swea changing box 5789

- input

```python
1 // Test Case 개수
5 2 // 첫 번째 Test Case, N=5, Q=2
1 3 // i = 1일 때, L=1, R=3
2 4	// i = 2일 때, L=2, R=4

```

- solve

```python
import sys
sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    # Test case N과 Q를 받아준다.
    N, Q = map(int, input().split())
    # N = 5
    # Q = 2
    # 카운트 갯수를 만들어준다.
    counts = [0] * N
    # N + 1까지 해보았는데 결과 값이
    # 1 0 1 2 2 2 0 으로 나와서
    # N 개까지만 해서 결과를 도출해보았다.
    # counts = [0, 0, 0, 0, 0]

    # for i in range(1, Q+1):
    #     L, R =map(int, input().split())
    #     for j in range(L-1, R):
    #         counts[j] += 1
    #         print(counts)
    for i in range(1, Q+1):
        # 조건에 i의 범위는 1<= i <= Q로 하였고
        L, R = map(int, input().split())
        # L, R의 값을 받는다.
        for j in range(L-1, R):
            counts[j] = i
            # L번 상자부터 R번 상자까지 값을 i로 변경
            # 처음에 더하는 줄 알아서 오답이 계속 나왔다.

    # 함수들의 +1, -1을 넣는 것에 따라
    # EOF when reading a line이 나올 수 있으니
    # N개의 counts의 값들의 변화
    # [1, 0, 0, 0, 0]
    # [1, 1, 0, 0, 0]
    # [1, 1, 1, 0, 0]
    # [1, 2, 1, 0, 0]
    # [1, 2, 2, 0, 0]
    # [1, 2, 2, 2, 0]

    print(f'#{test_case}', *counts)
    # 리스트 안의 값들만 표시하기 위해서 *counts 로 표현 하였다.
```