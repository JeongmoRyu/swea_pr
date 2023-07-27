# rest_num

```python
def solution(n):
    x = 1
    while x < n:
        if n%x == 1:
            break
        x += 1
    answer = x
    return answer
```