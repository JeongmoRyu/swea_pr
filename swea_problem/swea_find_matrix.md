# swea find matrix
1258
![image](https://swexpertacademy.com/main/common/fileDownload.do?downloadType=CKEditorImages&fileId=AV2Xif6qDlQBBASl)

input

```python
# example
2
5
1 2 3 4 0 
0 0 0 0 0 
5 0 0 0 0 
6 0 0 0 0 
0 0 0 0 0 
8
1 2 3 0 0 4 5 0 
6 7 8 0 0 0 0 0 
9 1 2 0 0 3 0 0 
4 5 6 0 0 7 0 0 
0 0 0 0 0 8 0 0 
9 1 2 3 0 4 0 0 
5 6 7 8 0 9 0 0 
0 0 0 0 0 0 0 0
```

```python
import sys
sys.stdin = open('input.txt', 'r')

T = int(input())

for test_case in range(1, T+1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]

    list_ans = []

    for i in range(N):
        for j in range(N):
            down_line = 0
            for a in range(i, N):
                # 뒤부분을 조사해준다.
                if arr[a][j] == 0:
                    # 0이면 더이상 진행하지 않는다.
                    break
                down_line += 1
                right_line = 0
                for b in range(j, N):
                    if arr[a][b] == 0:
                        # 0이면 더이상 진행하지 않는다.
                        break
                    right_line += 1
                    arr[a][b] = 0
                    # 한번 조사한 부분을 더 조사하지 않기 위해 초기화해준다.

            if right_line * down_line != 0:
                list_ans.append([down_line*right_line, down_line, right_line])
                # 순서대로 배치해야하기때문에 리스트를 만들어준다.

    # 넓이에 따른 bubble sort 정렬을 해준다.
    for i in range(len(list_ans) - 1):
        for j in range(len(list_ans) - i - 1):
            # 값이 같을 경우 행이 작은 것을 먼저 둔다. testcase 2개 틀림
            if list_ans[j][0] == list_ans[j][0]:
                if list_ans[j][1] > list_ans[j+1][1]:
                    list_ans[j], list_ans[j + 1] = list_ans[j + 1], list_ans[j]
            if list_ans[j][0] > list_ans[j+1][0]:
                list_ans[j], list_ans[j+1] = list_ans[j+1], list_ans[j]

    # 정답을 위한 새로운 리스트를 만들어 준다.
    ans = []
    for i in range(len(list_ans)):
        ans.append(list_ans[i][1])
        ans.append(list_ans[i][2])

    print(f'#{test_case} {len(list_ans)}', *ans)

```