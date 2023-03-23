# swea forth

4874

- input

```html
3
10 2 + 3 4 + * .
5 3 * + .
1 5 8 10 3 4 + + 3 + * 2 + + + .
```

- solve

```python
import sys
sys.stdin = open("forth_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    arr = input().split()
    new_stack = []
    num1 = 0
    # 스택 뒤에서 첫번째
    num2 = 0
    # 스택 뒤에서 두번째
    # print(arr)
    try:
        for a in range(len(arr)):
            if arr[a].isdigit():
                # if arr[a] == '1' and arr[a+1] == '0':
                #     new_stack.append(int(arr[a])*10)
                # elif arr[a] == '0' and arr[a-1] == '1':
                #     pass
                # else:
                new_stack.append(int(arr[a]))
            elif arr[a] == '+':
                num1 = new_stack.pop()
                num2 = new_stack.pop()
                new_stack.append(num1 + num2)
            elif arr[a] == '-':
                num1 = new_stack.pop()
                num2 = new_stack.pop()
                new_stack.append(num2 - num1)
            elif arr[a] == '*':
                num1 = new_stack.pop()
                num2 = new_stack.pop()
                new_stack.append(num1 * num2)
            elif arr[a] == '/':
                num1 = new_stack.pop()
                num2 = new_stack.pop()
                new_stack.append(num2 // num1)
            elif arr[a] == '.':
								# 총 갯수가 1이 아닐 수 도 있기에 그 부분에서 오류를 발생시켜주었다.
                if len(new_stack) == 1:
                    print(f'#{test_case}', *new_stack)
                else:
                    print(4/0)

    except:
        print(f'#{test_case} error')

    # print(f'#{test_case}', *new_stack)

```

- 함수를 사용한 풀이

```python
def calculate(left, right, operator)
    if operator == '+':
        return left + right
    if operator == '-':
        return left - right
    if operator == '*':
        return left * right
    if operator == '/':
        return left // right
    else:
        raise ValueError(f"wrong operator: {operator}")

OPS = "+-*/"

T = int(input())

for test_case in range(1, T + 1):
    expression = input().split()
    dig_stack = []

    for token in expression:
        # 수식 입력 종료
        if token == ".":
            # 계산할게 남아있다면 안된다.
            if len(dig_stack) == 1:
                print(f'#{test_case} {dig_stack.pop()}')
            else:
                print(f'#{test_case} error')
        # 연산자 입력인 경우
        elif token in OPS:
            # 연산할 숫자가 모자른다.
            if len(dig_stack) < 2:
                # 잘못된 수식이다.
                print(f'#{test_case} error')
                break
            # 아니라면 계산한다.
            operand_right = dig_stack.pop()
            operand_left = dig_stack.pop()
            # 계산 결과는 스택으로
            dig_stack.append(int(calculate(operand_left, operand_right, token)))
        # 위가 아니라면 다 숫자다.
        else:
            dig_stack.append(int(token))

```