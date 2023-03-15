
# swea_con_one 9386

- input
```
3
10
0011001110
10
0000100001
10
0111001111
```


- 풀이
```python
import sys
sys.stdin = open("input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    list_num = int(input())

    count = 0
    pos = 0
    X = []
    for a in range(len(str(list_num))-1):
        if str(list_num)[a] == '0':
            pos += 1
            continue
        elif str(list_num)[a] == '1':
            if str(list_num)[a] == str(list_num)[a+1]:
                count += 1
                X.append(count)
                if a == (len(str(list_num))-2) and str(list_num)[a+1] == '1':
                    count += 1
                    X.append(count)

            else:
                count += 1
                X.append(count)
                count = 0
    count = max(X)

    print(f'#{test_case} {count}')

```
- 다른풀이

```python

import sys

sys.stdin = open("input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    lst = list(map(int, input()))
    count = 0
    cnt = 0
    for i in range(N):
        if lst[i] == 0:
            cnt = 0
        else:
            cnt += 1
            if count < cnt:
                count = cnt
    print(f'#{test_case} {count}')

```