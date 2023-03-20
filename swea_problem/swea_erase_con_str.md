# swea_erase_con_str 4873

```python
3
ABCCB
NNNASBBSNV
UKJWHGGHNFTCRRCTWLALX
```

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

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
    def number(self):
        return self.top + 1

T = int(input())
for test_case in range(1, T+1):
    word = input()
    stack = Stack([''] * len(word))

    for char in word:
        if char == stack.peek():
            stack.pop()
        elif not char == stack.peek():
            stack.push(char)
    else:
        ans = stack.number()
        print(f'#{test_case} {ans}')
```