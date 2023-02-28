# swea_gravity 16090


input - 

```python
3
9
7 4 2 0 0 6 0 7 0
9
7 4 2 0 0 6 7 7 0
20
52 56 38 77 43 31 11 87 68 64 88 76 56 59 46 57 75 85 65 53
```

```python
import sys
sys.stdin = open("input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    
    N = int(input())
    box_list = list(map(int, input().split()))

    max_drop = 0
    for idx in range(N - 1):

        box_height = box_list[idx]

        tmp_drop = 0
        for j in range(idx + 1, N):
            if box_height > box_list[j]:
                tmp_drop += 1
        if max_drop < tmp_drop:
            max_drop = tmp_drop

    print(f'#{test_case}' + ' ' + f'{max_drop}')

   
```