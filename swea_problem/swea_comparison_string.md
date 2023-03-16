# swea comparison string 4864



- input

```python
3
XYPV
EOGGXYPVSY
STJJ
HOFSTJPVPP
ZYJZXZTIBSDG
TTXGZYJZXZTIBSDGWQLW
```

- solve

```python
import sys
sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    voca1 = str(input())
    voca2 = str(input())
    voca_list = []
    for i in range(len(voca2) - len(voca1) + 1):
        voca_list.append(voca2[i:i + len(voca1)])
    count = 0
    if voca1 in voca_list:
        count += 1

    ans = 0
    if count > 0:
        ans = 1
    print(f'#{test_case} {ans}')

```
