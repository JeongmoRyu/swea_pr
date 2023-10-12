# 두 큐의 합이 같게 만들기

처음 실패한 거

```python
def solution(queue1, queue2):
    sum_num = sum(queue1) + sum(queue2)
    int_num = int(sum_num // 2)
    if sum(queue1) == sum(queue2):
        return 0
    num = 0
    len_number = len(queue1) + len(queue2)
    while sum(queue1) != sum(queue2):
        if num >= len_number:
            return -1
        while queue2 and sum(queue1) < sum(queue2):
            A = queue2.pop(0)
            queue1.append(A)
            num += 1
            sum_queue1 = sum(queue1)
            sum_queue2 = sum(queue2)
            sum_queue2 -= A
            sum_queue1 += A
        while queue1 and sum(queue1) > sum(queue2):
            A = queue1.pop(0)
            queue2.append(A)
            num += 1
            sum_queue1 = sum(queue1)
            sum_queue2 = sum(queue2)
            sum_queue1 -= A
            sum_queue2 += A

    return num
```

stack과 queue에서 사용하기 위해 deque를 사용하고

while 안에 sum이 들어가 있어서 n**2급으로 시간이 걸려서 시간초과가 발생하고 있었다.

```python
from collections import deque

def solution(queue1, queue2):
    queue1 = deque(queue1)
    queue2 = deque(queue2)
    sum_queue1 = sum(queue1)
    sum_queue2 = sum(queue2)
    
    # sum_num = sum(queue1) + sum(queue2)
    # int_num = int(sum_num // 2)
    if sum_queue1 == sum_queue2:
        return 0
    num = 0
    len_number = len(queue1) + len(queue2)
    while sum_queue1 != sum_queue2:
        if num >= len_number:
            return -1
        while queue2 and sum_queue1 < sum_queue2:
            A = queue2.popleft()
            queue1.append(A)
            num += 1
            sum_queue2 -= A
            sum_queue1 += A
        while queue1 and sum_queue1 > sum_queue2:
            A = queue1.popleft()
            queue2.append(A)
            num += 1
            sum_queue1 -= A
            sum_queue2 += A

    return num
```
