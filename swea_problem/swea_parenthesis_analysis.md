# swea_parenthesis_analysis

고민을 더해보자

```python
import sys
sys.stdin = open('input.txt', 'r')

class Stack:
    def __init__(self, arr):
        self.arr = arr
        self.top = -1

    def push(self, item):
        self.top += 1
        self.arr[self.top] = item
    def pop(self):
        self.top -= 1
        return self.arr[self.top + 1]

    def is_empty(self):
        return self.top == -1

    def peek(self):
        return self.arr[self.top]

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    data = input()
    stack = Stack([0] * len(data))
    result = 0

    for i in range(len(data)):
        if stack.top == -1 and data[i] == '(':
            stack.push(data[i])
        elif data[i] == '(':
            stack.push(data[i])
        elif data[i] == ')':
            if stack.peek() == '(':
                stack.pop()
            else:
                break
        elif stack.pop == -1 and data[i] == ')':
            break
        elif stack.top == -1 and data[i] == '{':
            stack.push(data[i])
        elif data[i] == '{':
            stack.push(data[i])
        elif data[i] == '}':
            if stack.peek() == '{':
                stack.pop()
            else:
                break
        elif stack.pop == -1 and data[i] == '}':
            break
        else:
            continue
    else:
        if stack.is_empty():
            result = 1
    print(f'#{test_case} {result}')


```