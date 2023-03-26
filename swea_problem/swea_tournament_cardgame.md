#  swea_tournament_cardgame

16297

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4e188f50-ba39-408b-bbe9-d65e214287ff/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230326%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230326T035005Z&X-Amz-Expires=86400&X-Amz-Signature=0a51136fa366dd72d1769e81907f3d67a739d92957468be3776518e3d5ea8b88&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

input

```python
3
4
1 3 2 1
6
2 1 1 2 3 3
7
1 3 3 3 1 1 3
```

여러가지 시도

```python
# print(stack[0])
    # for i in range(N-1):
    #     if stack[0] == 3 and stack[1] == 1 or stack[0] == 1 and stack[1] == 3:
    #         num1 = stack.pop()
    #         num2 = stack.pop()
    #         stack.append('1')
    #     if stack[0] == '1' and stack[1] == '2' or stack[0] == '2' and stack[1] == '1':
    #         num1 = stack.pop()
    #         num2 = stack.pop()
    #         stack.append('2')
    #     if stack[0] == '3' and stack[1] == '2' or stack[0] == '2' and stack[1] == '3':
    #         num1 = stack.pop()
    #         num2 = stack.pop()
    #         stack.append('3')
    #     if stack[0] == '1' and stack[1] == '1':
    #         num1 = stack.pop()
    #         num2 = stack.pop()
    #         stack.append('1')
    #     if stack[0] == '2' and stack[1] == '2':
    #         num1 = stack.pop()
    #         num2 = stack.pop()
    #         stack.append('2')
    #     if stack[0] == '3' and stack[1] == '3':
    #         num1 = stack.pop()
    #         num2 = stack.pop()
    #         stack.append('3')
    # print(stack)
```

```python
import sys
sys.stdin = open('input.txt', 'r')

def game(a, b):
    num1 = arr[a - 1]
    num2 = arr[b - 1]
    if num1 == num2:
        return a
    elif num1 == 1:
        if num2 == 2:
            return b
        else:
            return a
    elif num1 == 2:
        if num2 == 3:
            return b
        else:
            return a
    elif num1 == 3:
        if num2 == 1:
            return b
        else:
            return a

def half_def(start, end):
    if start == end:
        return start
    else:
        mid = (start + end)//2
        a = half_def(start, mid)
        b = half_def(mid + 1, end)
        return game(a, b)

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    arr = list(map(int, input().split()))
    print(f'#{test_case} {half_def(1, N)}')

```

다른 풀이

나머지 기준으로 가위바위보를 하는 방법

```python
import sys
sys.stdin = open('input.txt', 'r')

T = int(input())

# 1 가위 2 바위 3 보
def battle(data, left, right):
    # 나머지 기준으로 승부를 가릴 수 있다.
    result = (data[left] - data[right]) % 3
    if result == 2:
        return right
    else:
        return left

# data 전체 카드들
# left 왼쪽 인덱스(0)
# right 오른쪽 인덱스(N-1)
def seperate(data, left, right):
    if left == right:
        return left

    mid = (left + right)//2
    left_group = seperate(data, left, mid)
    right_group = seperate(data, mid + 1, right)
    return battle(data, left_group, right_group)

for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    data = list(map(int, input().split()))
    result = seperate(data, 0, N-1)

print(f'#{test_case} {result + 1}')
```

