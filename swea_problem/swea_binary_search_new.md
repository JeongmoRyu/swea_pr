# swea binary search new

- 5207
- 16755

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2cb71e98-8d3f-4dae-812a-83c927ca9298/Untitled.png)

- input

```
3
3 3
1 2 3
2 3 4
3 5
1 3 5
2 4 6 8 10
5 5
1 3 5 7 9
1 2 3 4 5
```

- solve

```python
# 5207

import sys
sys.stdin = open('sample_input1.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N, M = map(int, input().split())
    list_n = sorted(list(map(int, input().split())))
    list_m = list(map(int, input().split()))

    count = 0

    def b_s(l, r, target, direction):
        global count
        global list_n
        m = (l + r) // 2
        if target == list_n[m]:
            count += 1
            return
        elif target > list_n[m]:
            if direction == 'R':
                return
            b_s(m + 1, r, target, "R")
        elif target < list_n[m]:
            if direction == "L":
                return
            b_s(l, m - 1, target, "L")

    for i in range(len(list_m)):
        b_s(0, N-1, list_m[i], "START")

    print(f'#{test_case} {count}')

```