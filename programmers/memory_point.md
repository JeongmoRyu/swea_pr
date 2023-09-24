# memory_point

- 첫번째 풀이
    - 정답은 나오는데 run time error가 나온다

```python
def solution(name, yearning, photo):
    answer = []
    ans_num = 0
    i = 0
    while i <= len(photo):
        for k in range(len(name)):
            ans_num += photo[i].count(name[k])*yearning[k]
        answer.append(ans_num)
        ans_num = 0
        i += 1
    return answer
```

- 두번째 풀이

```python
def solution(name, yearning, photo):
    answer = []
    ans_num = 0
    i = 0
    for i in range(len(photo)):
        for j in range(len(name)):
            if name[j] in photo[i]:
                ans_num += yearning[j]
        answer.append(ans_num)
        ans_num = 0

    return answer
```
