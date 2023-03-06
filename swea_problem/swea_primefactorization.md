# swea_primefactorization 1945

- input
```
10  
6791400
1646400
1425600
8575
185625
6480
1185408
6561
25
330750
```



- solve

```python

import sys
sys.stdin = open("input2.txt", "r")

divs = [2, 3, 5, 7, 11]
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, 11):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    cnts = [0]*len(divs)

    for i in range(len(divs)):
        while N%divs[i] == 0:
            cnts[i] += 1
            N = N//divs[i]

    print(f'#{test_case}', *cnts)
```