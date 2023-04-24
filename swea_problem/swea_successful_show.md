# successful show
 4789
 
input

```python
4
11111
09
110011
1
```

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    arr = list(input())

    count = 0
    sum_num = 0
    for i in range(len(arr)):
        for j in range(i):
            sum_num += int(arr[j])

        if sum_num < i:
            arr[j] = str(int(arr[j]) + i - sum_num)
            count += i - sum_num
        sum_num = 0

    print(f'#{test_case} {count}')
```