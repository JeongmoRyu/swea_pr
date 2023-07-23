# next_num

```jsx
def solution(common):
    
    diff = common[1] - common[0]
    if common[0] != 0:    
        div = common[1]//common[0]
    ans = 0
    for i in range(1, 2):
        if common[i+1] - common[i] != diff:
            ans = 1
            
    if ans == 0:
        answer = common[-1] + diff
    else:
        answer = common[-1]*div

    return answer
```