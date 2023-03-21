# swea_calculator3 1224


input3

```python
113
(9+(5*2+1)+(3*3*7*6*9*1*7+1+8*6+6*1*1*5*2)*4*7+4*3*8*2*6+(7*8*4*5)+3+7+(2+6+5+1+7+6+7*3*(6+2)+6+6)*2+4+2*2+4*9*3)
85
(4+8+4*(8*5*(7*(6*8)+3+(6+(3+7+1*7*5*4)*3)*2*3+5)+6+7*7)*4+2+9*4+7+2*3*(7*6*1*8)+9+9)
97
(9*5+7+8+6+3+9*2+1+7+4+3+9*3*1+4*(4+4*3*1+9*3+(9*5)*1*7*8+2+8+8*7+9*4*9)+(1+1*8+8*9*7+1*4*5*2*5))
89
((3*1*4+6*3+8+4+5+4+2*1+5+3*4)*1+1+(3*2*2+9+5*4*6*9+9+4+1*8+9)*4*8+9+3*7+9*6*9*5+8+3*8+1)
125
(2+(6*5+6+5+3*9+6+2+8*2+2)+6+2*2+2*5*1*2+1*8+1*(4+7*5+8+9+7+3*8*5)+(2+9+5*4*4+1+3*9*6*4*5+(5*(3+4)*9+8+7+9*2)+7+7+2)+8+2+7+5)
113
(8+8*6+3*9*8*7*6*3+5*(7*6*6+3*5+2*4*9*3+5+2+1*4)*1*7+6*8+9+3+2+8*3+8*(2+6*9+2*2*7+8*1*2+9*3+1+5)*(5*8+4*1*2*4*2))
115
(7+9*2+6+5*7+1*7*(9+8+6)*1*2+7+5*9*6*3+4*8*9*6*1*3+7*1+2+5+1*4*9+6*4+7*1*2*4*2+3+((3*4+9+7*1+7+5+3*7*1*7+8*3*8)+7))
99
(9*4+(1+5*7*8+9+1+2)+5+(6*(7+4*5*2+4+8*4+7)+9)*1*3*1+1*2*8+3+(2+9*(1*5*9+7*1+1+7+3*2))+1+3*7*8+9*6)
75
(2*2+((7+8*8*6+(6*6)*7+7*1)*5)*7+3+1*5+1*8*4+(9+6+(7*5+3+1*8*8*9+4+7+9)*3))
117
(8+6*9+2*3+4+2+(6+9+3+7*5*1+2+2+2)*9+4+6*1+6*4+7+7*2+5+2*6*(8*9*8*6+4*2)*5+5*8*3+(6+1+3+3*8*1*2*1+5+6)+1+5+4*7*1*3+1)

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