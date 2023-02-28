# swea_mutiple_card 16126

input

```python
3
5
49679
5
08271
10
7797946543
```

```python

import sys
sys.stdin = open("sample_input1.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    c = [0]*10
    # 카드에 들어갈 수가 한자리 수 자연수이기에 10개를 잡아준다.
    list_card = list(map(int, input().split()))
    # input 받은 데이터를 split하여 입력한다.
    for x in range(len(list_card)):
        for y in range(N):
            c[list_card[x]%10] += 1
            list_card[x] //= 10
        #진행 방식입니다.
        # c[9] = 1
        # c[7] = 1
        # c[6] = 1
        # c[9] = 2
        # c[4] = 1
        # [0, 0, 0, 0, 1, 0, 1, 1, 0, 2]
        # [1, 1, 1, 0, 0, 0, 0, 1, 1, 0]
        # [0, 0, 0, 1, 2, 1, 1, 3, 0, 2]

    list_max = []
    # 최대값을 가지는 여래 개의 리스트를 구한다.
    for x in range(len(list_card)):
        for a in range(10):
            # 0 부터 9까지의 10의 범위를 가진다.
            if c[a] == max(c):
                list_max.append(a)
    print(f'#{test_case} {max(list_max)} {max(c)}')

    # ///////////////////////////////////////////////////////////////////////////////////

```