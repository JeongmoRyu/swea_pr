# swea easy change

1970

```
N이 32850일 경우,
50,000 원 : 0개
10,000 원 : 3개
5,000 원 : 0개
1,000 원 : 2개
500 원 : 1개
100 원 : 3개
50 원 : 1개
10 원 : 0개

```
input

```python
10
32850
160
562410
148950
1000000
16540
30
10
66660
999990
```

```python
import sys
sys.stdin = open('input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = [0]*8

    if N>=50000:
        arr[0] = N//50000
        N -= arr[0]*50000
    if N>=10000:
        arr[1] = N//10000
        N -= arr[1]*10000
    if N>=5000:
        arr[2] = N//5000
        N -= arr[2]*5000
    if N>=1000:
        arr[3] = N//1000
        N -= arr[3]*1000
    if N>=500:
        arr[4] = N//500
        N -= arr[4]*500
    if N>=100:
        arr[5] = N//100
        N -= arr[5]*100
    if N>=50:
        arr[6] = N//50
        N -= arr[6]*50
    if N < 50:
        arr[7] = N//10
    print(f'#{test_case}')
    print(*arr)
```