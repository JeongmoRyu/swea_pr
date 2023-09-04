# missile

```python
def solution(targets):
    arr = sorted(targets)
    destination = arr[0][1]
    answer = 1
    for i in range(1, len(arr)):
        if arr[i][0] >= destination:
            answer += 1
            destination = arr[i][1]
        elif arr[i][1] <= destination:
            destination = arr[i][1]
    return answer
```
