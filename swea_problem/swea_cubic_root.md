# swea_cubic_root

5688
- input

```python

3
27
7777
64
```
- solve
```python
# 1번 풀이
import sys

sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T + 1):
    num = int(input())
    ans = -1
    for i in range(10**6 + 1):
        if i*i*i == num:
            ans += i + 1
            break
		print(f'#{test_case} {ans}')
```

만약 범위를 num으로 하면 숫자가 너무 크기떄문에 runtime error가 뜰 수 있다. 이를 해결하기 위해 3제곱하였을 때 최대로 나올 수 있는게 범위의 세제곱근이 되는 수가 10**6이기에 10**6 +1 까지 찾아본다.

pass

- solve

```python
# 2번 풀이
import sys

sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T + 1):
    num = int(input())

    B = round(num ** (1 / 3), 1)
    C = round(num ** (1 / 3))
    if B == C:
        print(f'#{test_case} {C}')
    else:
        print(f'#{test_case} -1')
#
```

100 testcase 중 99개 정답

혹시 몰라 A = round(num **(1/3), 2) 까지 해줬지만 99개 정답

한 개가 멀까?

```python

for test_case in range(1, T+1):
		N = int(input())
		X = None
```