# swea_go_back_to_my_room 4408

- input

```python
3
4
10 20
30 40
50 60
70 80
2
1 3
2 200
3
10 100
20 80
30 50

```
- solve

```python
import sys
sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    cnts = [0]*200
    for _ in range(N):
        s, e = map(int, input().split())
        if s > e:
            s, e = e, s
        for i in range((s-1)//2, (e-1)//2+1):
            cnts[i] += 1
        ans = max(cnts)
    print(f'#{test_case} {ans}')
```