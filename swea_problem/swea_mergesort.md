# swea mergesort

5204

- input

```python
2
5
2 2 1 1 3
10
7 5 4 1 2 10 3 6 9 8
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

def merge_sort(numbers):
    global ans
    if len(numbers) == 1:
        return numbers

    mid = len(numbers)//2
    left_numbers = merge_sort(numbers[:mid])
    right_numbers = merge_sort(numbers[mid:])

    left_idx = right_idx = k = 0

    while left_idx < len(left_numbers) and right_idx < len(right_numbers):
        if left_numbers[left_idx] < right_numbers[right_idx]:
            numbers[k] = left_numbers[left_idx]
            left_idx += 1
        else:
            numbers[k] = right_numbers[right_idx]
            right_idx += 1
        k += 1

    if left_idx < len(left_numbers):
        numbers[k:] = left_numbers[left_idx:]
    if right_idx < len(right_numbers):
        numbers[k:] = right_numbers[right_idx:]

    if left_numbers[-1] > right_numbers[-1]:
        ans += 1
    return numbers

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = list(map(int, input().split()))
    ans = 0

    merge_sort(arr)
    # print(arr)
    print(f'#{test_case} {arr[N//2]} {ans}')
```