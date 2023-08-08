# binary

```python

def solution(s):
    count = 0
    count_z = 0
    while s != '1':
        count_one = 0
        print(str(s))
        for i in range(len(str(s))):

            if s[i] == '1':
                count_one += 1
        count_z += len(s) - count_one
        s = bin(count_one)[2:]
        print(s)
        count += 1

    answer = []
    answer.append(count)
    answer.append(count_z)
    return answer

print(solution(s))

```