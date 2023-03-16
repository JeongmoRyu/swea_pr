# swea num of string 4865



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
    for i in range(len(voca1)):
        voca_list.append(voca1[i])
    voca = []
    for i in voca_list:
        if i not in voca:
            voca.append(i)
    # print(voca)
    list_word = []
    for word in voca2:
        for a in range(len(voca)):
            if voca[a] == word:
                list_word.append(voca[a])
    # print(list_word)
    count_list = []
    for a in range(len(list_word)):
        count_list.append(list_word.count(list_word[a]))
    # print(count_list)

    print(f'#{test_case} {max(count_list)}')

```