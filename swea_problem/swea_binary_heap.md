# swea binary heap
16531

- input

```python
3
6
7 2 5 3 4 6
6
3 1 4 16 23 12
8
18 57 11 52 14 45 63 40
```
- solve

```python
import sys
sys.stdin = open('sample_input (1).txt', 'r')

# 삽입
def enq(n):
    global last
    # 완전 이진트리에 마지막 정점을 추가하고
    last += 1
    # 마지막 정점에 저장
    heap[last] = n
    # 부모가 있고, 부모 > 자식
    parent = last
    child = parent//2
    # 부모가 존재하고 부모
    while parent > 0 and heap[parent] < heap[child]:
        heap[parent], heap[child] = heap[child], heap[parent]
        # 옮긴 자리에서 부모와 비교하기 위해
        parent = child
        child = parent//2
    return

T = int(input())

for test_case in range(1, T+1):
    N = int(input())

    arr = list(map(int, input().split()))

    heap = [0] *(N+1)
    last = 0
    for i in range(len(arr)):
        enq(arr[i])
    # print(heap)
    ans = last
    list_ans = []
    while ans != 1:
        ans = ans//2
        list_ans.append(heap[ans])

    print(f'#{test_case} {sum(list_ans)}')
```