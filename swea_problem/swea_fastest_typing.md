# swea_fastest_typing 3143

- input


```
2
banana bana
asakusa sa

```
- solve


```python
import sys
sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    A, B = map(str, input().split())

    # count = 0
    # word_list = []
    # for i in range(len(A) - len(B) + 1):
    #     word_list.append(A[i:i + len(B)])
    #     if B == word_list[i]:
    #         count += 1

    # word_list = []
    # for i in range(len(A) - len(B) + 1):
    # word_list.append(A[i:i + len(B)])
    # count = 0
    # for j in range(len(word_list)):
    #     if B == word_list[j]:
    #         count += 1

    # ans = len(A) - count*(len(B)-1)

    # 이러한 방식으로 풀어보았는데 존재하는지 찾을때는 충분히 도움이 되지만
    # 예를 들어 A = sasasasasassassas B = sas 이런식으로 중복으로
    # 겹치게 되면 문제가 발생하는 것을 알 수 있었다.

    num = A.count(B)
    # 이것도 되는걸 해보다가 깨닳았다......
    # god python!!!

    ans = len(A) - num * (len(B) - 1)

    print(f'#{test_case} {ans}')
```