# 연속된 부분 수열의 합

- 중간에 print가 들어가 있으면 출력 오류가 뜰 수 있다.
- 출력 크기 오류가 뜬 건 또 처음이네요 ㅋㅋㅋㅋ

```python
def solution(sequence, k):
    answer = []
    n = len(sequence)
    start,end = 0, 0
    for i in range(len(sequence)):
        while start < k and end < n:
            start += sequence[end]
            end += 1
        if start == k:
            answer.append((i,end-1))
        start -= sequence[i]
    new_list = [0]*len(answer)
    for i in range(len(answer)):
        new_list[i] = answer[i][1] - answer[i][0]
    answer_idx = new_list.index(min(new_list))
    
    return [answer[answer_idx][0], answer[answer_idx][1]]
```
