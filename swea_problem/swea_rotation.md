# swea rotation

16525

- input

```python

3
3 10
5527 731 31274 
5 12
18140 14618 18641 22536 23097 
10 23
17236 31594 29094 2412 4316 5044 28515 24737 11578 7907
```
- solve

```python
import sys
sys.stdin = open('../sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T + 1):
    N, M = map(int, input().split())
    list_num = list(map(int, input().split()))
    # 문제에서 추가되지 않고 그저 회전만하기 때문에
    # pop append를 사용해도되지만
    # M을 N으로 나누어준 나머지의 값의 위치가 정답이 될 것이다.
    print(f'#{test_case} {list_num[M % N]}')

```
