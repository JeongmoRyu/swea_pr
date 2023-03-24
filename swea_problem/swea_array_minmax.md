# swea_array_minmax 4881

input

```python
3
3
2 1 2
5 8 5
7 2 2
3
9 4 7
8 6 5
5 3 7
5
5 2 1 1 9
3 3 8 3 1
9 2 8 8 6
1 5 7 8 3
5 5 4 6 8
```

- 온갖 방법으로 도전해보았다 ㅠㅠ

```python 

# T = int(input())
# for test_case in range(1, T+1):
#     N = int(input())
#     arr = [list(map(int, input().split())) for _ in range(N)]
#
#     for i in range(N):

#
# import itertools
#
#
# T = int(input())
# for test_case in range(1, T+1):
#     N = int(input())
#     arr = [list(map(int, input().split())) for _ in range(N)]
#
#     right_row = []
#     for i in range(N):
#         for j in range(N):
#             right_row.append((i, j, arr[i][j]))
#     p = [n for n in range(0, N)]
#     x = list(itertools.permutations(p,N))
#     print(x)
    # ans = list(combinations(right_row, 3))
    # print(len(ans))
    # print(ans[-1])
    # print(ans[-1][0][0])
    # print(ans[-1][1][0])
    # print(ans[-1][2][0])

    # for a in range(len(ans)):
    #     if ans[a][0][0] == ans[a][1][0]:
    #         ans.remove(ans[a])
    #     if ans[a][0][0] == ans[a][2][0]:
    #         ans.remove(ans[a])
    #     if ans[a][1][0] == ans[a][2][0]:
    #         ans.remove(ans[a])
    #     if ans[a][0][1] == ans[a][1][1]:
    #         ans.remove(ans[a])
    #     if ans[a][0][1] == ans[a][2][1]:
    #         ans.remove(ans[a])
    #     if ans[a][1][1] == ans[a][2][1]:
    #         ans.remove(ans[a])
    # print(ans)
    # a = 0
    # while a < len(ans):
    #     if ans[a][0][0] == ans[a][1][0]:
    #         ans.remove(ans[a])
    #     if ans[a][0][0] == ans[a][2][0]:
    #         ans.remove(ans[a])
    #     if ans[a][1][0] == ans[a][2][0]:
    #         ans.remove(ans[a])
    #     if ans[a][0][1] == ans[a][1][1]:
    #         ans.remove(ans[a])
    #     if ans[a][0][1] == ans[a][2][1]:
    #         ans.remove(ans[a])
    #     if ans[a][1][1] == ans[a][2][1]:
    #         ans.remove(ans[a])
    #     a += 1
    #
    # print(ans[0][0][0])
    # print(ans[0][1][0])
    # print(ans[0])
    # # print(ans)
    # # print(ans)
    #
    # ans_list = []
    # ans_num = 0
    # for i in range(len(ans)):
    #     ans_num = ans[i][0][2] + ans[i][1][2] + ans[i][2][2]
    #     ans_list.append(ans_num)
    #     ans_num = 0
    # print(min(ans_list))
    # print(f'#{test_case} {ans_num}')
    # print(ans)
    # len_right_row = len(right_row)
    # bit = [0]*len_right_row
    # # f(0, len_right_row, 3)
    # print(right_row)
    # print(f'#{test_case}')
    # min_list = []
    #
    # for a in range(N):
    #     for b in range(N):

    # while True:
    #     if right_row[i][j]
    # for i in range(N):
    #     for j in range(N):
    #         right_row[i][j]

    # for j in range(N+1, 3*N):
    #     ans.append(min(right_row[j][2*N - 1]))

    # print(ans)
    # vertical_row = []
    # for j in range(N):
    #     for i in range(N):
    #         vertical_row.append((i, j, arr[i][j]))
    # print(right_row)
    # print(vertical_row)

    #
    # arr_num = []
    # min_cnt = []
    # for i in range(N):
    #     ans.append(min(arr[i]))
    #     min_cnt.append(count(min(arr[i])))
    #     for j in range(N):
    #         if arr[i][j] == min(arr[i]):
    #             arr_num.append((i, j))
    # X = []
    # print(arr_num[0][1])
    # # for a in range(len(arr_num))
    # #     if arr_num
    #
    # # for i in range(N):
    # #     for j in range(N):
    # #         if arr_num
    #             #     arr_num.append((i, j))
    #
    #
    # print(ans)
    # print(arr_num)
```

- backtracking 방법을 동원하여

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

def backtracking(row, score):
    global ans
    if ans <= score:
        return

    if row == N:
        ans = min(ans, score)

    for j in range(N):
        if v[j] == 0:
            v[j] = 1
            backtracking(row+1, score+arr[row][j])
            v[j] = 0

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    ans = N * 10
    v = [0] * N
    backtracking(0, 0)

    print(f'#{test_case} {ans}')
```

- 다른 풀이

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

# selected 리스트에 각 idx에 몇번째를 선택했는지 저장한다.
# 저장이 안된 항목은 아직 선택하지 않은 것
# 매번 DFS 마다 selected와 입력 N*N 행렬을 가지고 합을 구해보고,
# 여태까지 나온 결과 중 제일 작은 것 보다 커지면,
# 그때 return 을 해준다.
T = int(input())

def calculate_sum(arr, selected):
    temp_sum = 0
    for i in range(len(selected)):
        # selected[i]에는 i번째 줄에서 몇번째 칸을 골랐는지 저장되어 있다.
        temp_sum += arr[i][selected[i]]
    return temp_sum

# arr = 데이터
# selected = 각 줄의 몇 번째를 선택했는지
# row == 현재 찾아봐야 될 줄
# size ==  데이터의 크기(N)
def test_sum(arr, selected, row, size):
    global min_sum
    temp_sum = calculate_sum(arr, selected)
    if temp_sum > min_sum:
        return
    if row == size:

        # arr에서 selected를 기반으로 현재 최소를 구하자
        temp_sum = calculate_sum(arr,selected)
        min_sum = min(min_sum, temp_sum)
        return
    # i는 0에서 size-1 까지
    for i in range(size):
        if i in selected:
            # 이미 선택한 적 있는 인덱스다
            continue
            # 다음 인덱스 검사
        # 이번 줄에서 선택해서 다음줄로 넘기자
        selected.append(i)

        test_sum(arr, selected, row+1, size)
        selected.pop()

for test_case in range(1, T+1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    min_sum = 10 * N

    selected = []
    row = 0
    test_sum(arr, selected, row, N)
    print(f'#{test_case} {min_sum}')

```

- DFS방식으로 구현

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())

for test_case in range(1, T+1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    min_sum = 10*N
    selected = [-1 for _ in range(N)]
    stack =[]
    # 첫줄을 먼저 다 스택에 넣는다.
    for i in range(N-1, -1, -1):
        # (row, index)
        stack.append((0, i))
    # DFS start
    while stack:
        # 현재 검증하는 줄, 칸
        row, idx = stack.pop()
        # 현재 줄 이후는 다 -1
        for i in range(row, N):
            selected[i] = -1
        # 현재 줄의 몇번째 칸인지 기록
        selected[row] = idx
        # 부분 합 구해보기
        temp_sum = 0
        for i in range(row + 1):
            temp_sum += arr[i][selected[i]]

        # 만약 지금까지 합이 더 크면
        if temp_sum > min_sum:
            continue

        row += 1
        # 마지막 줄까지 확인함
        if row == N:
            # 결과 검증하고 다음 것 확인
            min_sum = min(min_sum, temp_sum)
            continue

        # 다음 줄 등록
        for i in range(N-1, -1, -1):
            if i not in selected:
                stack.append((row, i))

    print(f'#{test_case} {min_sum}')

```