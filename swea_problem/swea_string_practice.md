# swea string 1213

- input 
```
ex)
1
ti
vlslsjtititinalknleknvlkhlaenfasknvlsakjfalsjfseltitijnvalkdfkajlkdjflsakdjflasdhflasdfsldakftisdalvnaltildkfjalskjvlasdg

```
- solve

```python
import sys
sys.stdin = open("test_input.txt", encoding='utf-8')

T = 10
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    word = input()
    l_word = input()
    list_word = []
    ans = 0
    for i in range(len(l_word) - len(word) + 1):
        list_word.append(l_word[i:i + len(word)])
    for j in range(len(list_word)):
        if word == list_word[j]:
            ans += 1

    print(f'#{N} {ans}')
```