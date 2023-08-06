# need money

```python
def solution(price, money, count):
    answer = 0
    need_money = price * count * (count + 1) / 2
    if need_money > money:
        answer = need_money - money
    
    return answer
```