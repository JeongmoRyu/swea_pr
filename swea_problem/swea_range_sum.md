# swea_rangesum(16071)

- 첫번째 풀이
```python
import sys
sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    n, m = list(map(int, input().split()))
    num_list = list(map(int, input().split()))
    # input을 받는 것을 int로 split하여 리스트로 구성한다.
    # N input 또한 2개이므로 2개의 input 리스트로 split하여 구성한다.
    max_sum = 0
    min_sum = 0
    for a in range(len(num_list)):
        min_sum += num_list[a]
    #리스트의 모든 합보다 작을 수 밖에 없기에 min으로 둔다.

    # 리스트의 구간을 정해준다.
    for a in range(n-m+1):
        num_amo = 0
        # N의 두번째 개수의 합을 구한 리스트를 구성한다.
        for b in range(m):
            num_amo += num_list[a + b]

        # 큰 수가 들어오면 큰 수로 바뀌고
        if max_sum < num_amo:
            max_sum = num_amo
        # 작은 수가 들어오면 작은 수로 변환한다.
        if min_sum > num_amo:
            min_sum = num_amo

    print(f'#{test_case} {max_sum - min_sum}')
```


- 다른 풀이 방법

```python
import sys
sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    n, m = list(map(int, input().split()))
    list_num = list(map(int, input().split()))
    # input을 받는 것을 int로 split하여 리스트로 구성한다.
    # N input 또한 2개이므로 2개의 input 리스트로 split하여 구성한다.
    max_sum = 0
    min_sum = 0

    # 리스트의 구간을 정해준다.
    for a in range(0, n-m+1):
        num_amo = 0
        # N의 두번째 개수의 합을 구한 리스트를 구성한다.
        for b in range(m):
            num_amo += list_num[a + b]
        if a == 0:
            min_sum, max_sum = num_amo, num_amo
        # 큰 수가 들어오면 큰 수로 바뀌고
        if max_sum < num_amo:
            max_sum = num_amo
        # 작은 수가 들어오면 작은 수로 변환한다.
        if min_sum > num_amo:
            min_sum = num_amo

    print(f'#{test_case} {max_sum - min_sum}')
```


input
```python
3

10 3

1 2 3 4 5 6 7 8 9 10

10 5

6262 6004 1801 7660 7919 1280 525 9798 5134 1821

20 19

3266 9419 3087 9001 9321 1341 7379 6236 5795 8910 2990 2152 2249 4059 1394 6871 4911 3648 1969 2176
```