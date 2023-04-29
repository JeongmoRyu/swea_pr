# swea cheolsu's mistake

13389

![image](https://swexpertacademy.com/main/common/fileDownload.do?downloadType=CKEditorImages&fileId=AX2eRmDKiEsDFAW0)

- input

```python
5
hello 9
aaaa 3
apple 4
aaabbb 6
bb 3
```

- solve

```python
# 13389 철수의 실수

import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())

for test_case in range(1, T+1):
    arr, K = map(str, input().split())
    num = int(K)

    list_arr = []
    I = 0
    while I != len(arr):
        if len(list_arr) == 0:
            list_arr.append(arr[I])
            I += 1
        elif list_arr[-1] != arr[I]:
            list_arr.append(arr[I])
            I += 1
        elif list_arr[-1] == arr[I]:
            list_arr.append('A')

    for i in range(len(list_arr)):
        if list_arr[i] == 'A':
            list_arr[i] = 'a'

    # print(list_arr)

    num_list = [0, 'a', 'b', 'c', 'd','e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']
    for i in range(len(list_arr)):
        for j in range(len(num_list)):
            if list_arr[i] == num_list[j]:
                list_arr[i] = j

    # print(list_arr)
    big_num = 0
    for i in range(len(list_arr)):
        big_num += list_arr[i]*(26**(len(list_arr)-(i+1)))
    # print(big_num)
    code = []
    for i in range(len(str(big_num))):
        code.append(str(big_num)[i])
    # print(code)
    for i in range(len(code)):
        if i%2==0:
            code[i] = str(int(code[i]) - num)
        else:
            code[i] = str(int(code[i]) + num)
    # print(code)
    for i in range(len(code)):
        if int(code[i]) >= 0:
            if len(code[i]) >= 2:
                X = 0
                for j in range(len(code[i])):
                    X += int(code[i][j])
                list_new = [str(X) + 'D' + '1']
                code[i] = ''.join(list_new)
            else:
                list_new = [code[i] + 'D' + '0']
                code[i] = ''.join(list_new)
        elif int(code[i]) < 0:
            if len(code[i]) >= 3:
                Y = 0
                for j in range(1, len(code[i])):
                    Y -= int(code[i][j])
                list_new = [str(Y) + 'D' + '1']
                code[i] = ''.join(list_new)
            else:
                list_new = [code[i] + 'D' + '0']
                code[i] = ''.join(list_new)

    print(f'#{test_case}', ' '.join(code))

```