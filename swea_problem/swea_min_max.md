# swea_min_max(16068)

```python
# import sys
# sys.stdin = open("../sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    num_list = list(map(int, input().split()))

    for a in range(N-1, 0, -1):
        for b in range(0, a):
            if num_list[b] > num_list[b + 1]:
                num_list[b], num_list[b + 1] = num_list[b + 1], num_list[b]
    print('#' + f'{test_case}' + ' ' + str(num_list[-1] - num_list[0]))
```



input
```python 
3

5

477162 658880 751280 927930 297191

5

565469 851600 460874 148692 111090

10

784386 279993 982220 996285 614710 992232 195265 359810 919192 158175
```