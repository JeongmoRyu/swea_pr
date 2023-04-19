# swea new insomnia therapy

1288

input

```python
5
1
2
11
1295
1692
```

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N = input()
    number = [0 for _ in range(10)]
    list_number = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    
    count = 0
    while 0 in number:
        count += 1
        N = int(N) * count
        N = str(N)
        for i in range(len(N)):
            for j in range(10):
                if int(N[i]) == list_number[j]:
                    number[j] += 1
        N = int(N)//count

    print(f'#{test_case} {N*count}')
   
```