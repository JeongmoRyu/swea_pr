# babytalk

```jsx
from itertools import permutations
def solution(babbling):
    answer = 0
    museek = ["aya","ye","woo","ma"]
    word = []
    for i in range(1, len(museek)+1):
        for j in permutations(museek, i):
            word.append(''.join(j))

    for i in babbling:
        if i in word:
            answer += 1

    return answer
```