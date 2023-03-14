# swea_초심자의 회문 검사

- input

```python
10
level
samsung
eye
exo
ioi
blackpink
hannah
B1A4
linetown
nursesrun
```
<br/>

- solve
<br/>

```python
import sys
sys.stdin = open("../input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    word = str(input())

    result = ''
    for char in word:
        result = char + result
    def ans():
        if word == result:
            return 1
        else:
            return 0
    print(f'#{test_case} {ans()}')
```