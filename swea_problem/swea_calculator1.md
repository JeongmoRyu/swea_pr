# swea_calculator1 1222


input cal1

```python
101
9+8+5+9+2+4+1+8+3+9+3+8+7+8+6+8+9+4+1+1+7+6+1+5+8+7+6+9+6+3+1+3+1+7+5+9+2+8+4+3+7+3+4+7+3+4+8+3+2+6+6
83
7+4+8+3+4+8+5+5+3+6+7+1+2+5+6+5+5+6+1+6+7+8+6+4+7+4+3+1+6+1+2+1+6+8+6+9+2+7+4+3+2+3
119
9+4+7+9+1+3+5+4+7+4+1+3+3+4+9+9+6+2+7+7+3+4+4+7+2+7+9+7+9+9+4+5+9+2+9+8+4+8+8+2+4+6+8+7+5+3+7+7+6+9+8+3+3+4+6+8+3+8+7+9
61
3+7+9+5+6+4+9+3+4+2+1+3+6+5+3+6+5+7+1+7+7+4+5+2+1+9+2+4+3+7+9
67
9+3+8+7+2+6+1+1+3+8+2+9+3+9+1+9+3+5+3+2+1+6+2+4+3+5+6+1+2+7+7+5+4+2
83
6+1+4+4+7+6+3+9+6+9+2+5+7+7+8+8+9+6+2+3+3+9+7+2+5+1+3+7+9+4+7+3+2+9+3+3+8+1+4+4+3+4
63
4+5+3+3+1+2+9+9+3+9+9+7+5+6+1+1+7+1+8+8+2+9+8+8+8+7+7+5+9+3+4+9
89
6+1+2+1+6+8+6+8+8+9+5+7+2+1+3+4+8+5+2+2+5+5+4+8+5+3+4+5+9+5+9+2+9+4+7+2+6+8+9+6+3+2+1+2+4
69
6+3+3+1+8+2+4+2+5+5+4+9+2+2+1+3+5+9+3+6+4+7+1+9+1+9+3+4+2+7+2+6+9+6+5
65
4+3+6+8+9+5+9+4+4+9+1+9+8+9+9+2+4+6+8+6+9+5+3+9+7+3+9+5+6+5+9+7+5
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