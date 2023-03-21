# swea_calculator2 1223

input2

```python
101
9+5*2+1+3*3*7*6*9*1*7+1+8*6+6*1*1*5*2*4*7+4*3*8*2*6+7*8*4*5+3+7+2+6+5+1+7+6+7*3*6+2+6+6*2+4+2*2+4*9*3
79
4+4*3*4*9+2+7*4*7+7*7*9*5*2+8*8+2*6*7*3*7*9*3*4+8+8*9+3+9+6+9+4*1+6*3+5+1+7+5*1
113
2+3+9*9+8+2*1+3*2*3*1+3*3+1+2+3*6*2*7*4+9+1+4+6+9*9*5+7+8+6+3+9*2+1+7+4+3+9*3*1+4*4+4*3*1+9*3+9*5*1*7*8+2+8+8*7+9
89
4*9+1+1*8+8*9*7+1*4*5*2*5+8*3*5+5+2*4+2+8+6*2*2+9+3*1*2+2*5+9*2*3*9+6+7*9+9*4+7+6+6*6+3+8
77
5+4+9+9*9*2+6*6*5+9+3*5+5*7*8*3*7*1*9*9+8+3+8*9*6+2*9*3+6*5+6*7*2+5+5*3+4*6+7
119
5+7+1+6+3+6*7+7+5*5*3*5*6*9+5*9*5*9+8+8+5*1*6*2+3+2+8+6+2+2*3*4+5*8*3*6*2*9+1*7*7*4*2+2*5+6+7+2*7*4+9*6*4*3*1*3*5+3*7+8
115
8*6+3*9*8*7*6*3+5*7*6*6+3*5+2*4*9*3+5+2+1*4*1*7+6*8+9+3+2+8*3+8*2+6*9+2*2*7+8*1*2+9*3+1+5*5*8+4*1*2*4*2*6*3*8*8+4+1
91
5*8*4+5*7+9*2+6+5*7+1*7*9+8+6*1*2+7+5*9*6*3+4*8*9*6*1*3+7*1+2+5+1*4*9+6*4+7*1*2*4*2+3+3*4+9
107
7*1+7+5+3*7*1*7+8*3*8+7+3*2*6*2+3+6*4+3+8+9*4+1+5*7*8+9+1+2+5+6*7+4*5*2+4+8*4+7+9*1*3*1+1*2*8+3+2+9*1*5*9+7
109
1+1+7+3*2+1+3*7*8+9*6+1+8*3*7+8*5*7*7+4*3*7*4+7+3+2*2+7+8*8*6+6*6*7+7*1*5*7+3+1*5+1*8*4+9+6+7*5+3+1*8*8*9+4+7
```



```python

import sys
sys.stdin = open("../cal_input.txt", "r")

# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, 11):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    arr = input()

    stack = []
    # 출력문자열
    result = ''

    # 한글자씩 알아보자
    for token in arr:
        if token.isdecimal():
            result += token
        else:
            # 첫 연산자
            if not stack:
                # 기록
                stack.append(token)
            elif token == '(':
                # 무조건 push
                stack.append(token)
            elif token in '*/':
                # last_operator = stack[-1]
                # 나보다 느린애가 나올때 까지
                while stack and stack[-1] in '*/':
                    result += stack.pop()
                # 그다음 나
                stack.append(token)
            elif token in '+-':
                # 더하기 빼기는 여는 괄호보다만 빠르다.
                while stack and stack[-1] != '(':
                    result += stack.pop()
                stack.append(token)
            # 닫는 괄호
            elif token == ')':
                while stack and stack[-1] != '(':
                    result += stack.pop()
                stack.pop()
                # 남는 괄호는 버린다.
        # 아직 계산 안한 남은 연산자
    while stack:
        result += stack.pop()
    # print(result)
    # print(result[0])
    # print(type(result[0]))
    new_stack = []
    num1 = 0
    # 스택 뒤에서 첫번째
    num2 = 0
    # 스택 뒤에서 두번째

    for a in range(len(result)):
        if result[a].isdigit():
            new_stack.append(int(result[a]))
        elif result[a] == '+':
            num1 = new_stack.pop()
            num2 = new_stack.pop()
            new_stack.append(num1 + num2)
        elif result[a] == '-':
            num1 = new_stack.pop()
            num2 = new_stack.pop()
            new_stack.append(num2 - num1)
        elif result[a] == '*':
            num1 = new_stack.pop()
            num2 = new_stack.pop()
            new_stack.append(num1 * num2)
        elif result[a] == '/':
            num1 = new_stack.pop()
            num2 = new_stack.pop()
            new_stack.append(num2 // num1)

    print(f'#{test_case}', *new_stack)

```