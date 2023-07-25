# square num

```python
def solution(n):
    answer = 0
    num = 0
    while num < 1001:
        if num**2 == n:
            answer = 1
            break
        else:
            answer = 2
        num += 1
    return answer
```