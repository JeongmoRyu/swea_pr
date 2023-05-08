# baby gin1

5203

- input

```
3
9 9 5 6 5 6 1 1 4 2 2 1
5 3 2 9 1 5 2 0 9 2 0 0
2 8 7 7 0 2 2 2 5 4 0 3

```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    arr = list(map(int, input().split()))
    list_first = []
    list_second = []
    triple1 = 0
    Run1 = 0
    triple2 = 0
    Run2 = 0
    answer = 0
    c1 = [0] * 11
    c2 = [0] * 11

    for i in range(len(arr)):
        if i % 2 == 0:
            list_first.append(arr[i])
            c1[arr[i]] += 1
            for j in range(len(c1)):
                if c1[j] >= 3:
                    triple1 += 1
            k = 0
            while k < 10:
                if c1[k] >= 1 and c1[k + 1] >= 1 and c1[k + 2] >= 1:
                    Run1 += 1
                k += 1
            if triple1 == 0 and triple2 == 0 and Run1 == 0 and Run2 == 0:
                answer = 0
            elif triple1 > 0 or Run1 > 0:
                answer = 1
                break
            elif triple2 > 0 or Run2 > 0:
                answer = 2
                break

        else:
            list_second.append(arr[i])
            c2[arr[i]] += 1
            for j in range(len(c2)):
                if c2[j] >= 3:
                    triple2 += 1
            k = 0
            while k < 10:
                if c2[k] >= 1 and c2[k + 1] >= 1 and c2[k + 2] >= 1:
                    Run2 += 1
                k += 1
            if triple1 == 0 and triple2 == 0 and Run1 == 0 and Run2 == 0:
                answer = 0
            elif triple1 > 0 or Run1 > 0:
                answer = 1
                break
            elif triple2 > 0 or Run2 > 0:
                answer = 2
                break

    print(f'#{test_case} {answer}')
```