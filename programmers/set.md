# set 짝지어 제거하기


```python
def solution(s):
    list_ans = [s[0]]
    answer = 0
    for i in range(1, len(s)):
        if len(list_ans) == 0:
            list_ans.append(s[i])
        else:
            if list_ans[-1] == s[i]:
                list_ans.pop(-1)
            else:
                list_ans.append(s[i])

    if len(list_ans) == 0:
        answer = 1

    return answer
```
