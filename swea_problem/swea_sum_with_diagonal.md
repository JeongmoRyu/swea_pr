# swea_sum_with_diagonal 4837


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
sys.stdin = open("sum_input.txt", "r")

# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, 11):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())

    arr = [list(map(int, input().split())) for _ in range(100)]
    # for x in range(100):
    #     arr.append(list(map(int, input().split())))
    # 각 줄의 합을 sum_list에 넣는다.
    # 가로의 합을 sum_list에 넣는다.
    sum_right = []
    for i in range(100):
        right_row = 0
        for j in range(100):
            right_row += arr[i][j]
        sum_right.append(right_row)

    # 세로의 합을 sum_list에 넣는다.
    vertical_list = []
    for i in range(100):
        down_row = 0
        for j in range(100):
            down_row += arr[j][i]
        vertical_list.append(down_row)

        # 합을 sum_list에 넣는다.
    left_rec =[]
    left_total = 0
    for a in range(100):
        left_total += arr[a][a]
    left_rec.append(left_total)
        
    right_rec =[]
    right_total = 0
    for c in range(100):
        right_total += arr[c][99 - c]
    right_rec.append(right_total)
    sum = []
    sum = sum_right + vertical_list + left_rec + right_rec

    max_sum = sum[0]
    for i in range(len(sum)):
        if sum[i] > max_sum:
            max_sum = sum[i]

    # 테스트 케이스별 최고치들을 정답으로 적는다.
    print(f'#{test_case} {max_sum}')

```