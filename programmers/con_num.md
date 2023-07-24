# con num

```python
def solution(num, total):
    answer = []
    if num % 2 == 1:
        center = total//num
        for i in range(center - (num//2), center + (num//2) + 1):
            answer.append(i)
    else:
        center = total//num
        for i in range(center - ((num-2)//2), center + ((num-2)//2) + 2):
            answer.append(i)
            
    return answer
```