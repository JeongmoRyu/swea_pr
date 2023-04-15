# swea binary num

input

```python
3
4 47FE
5 79E12
8 41DA16CD
```

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

# 16745.5185

T = int(input())
for test_case in range(1, T+1):
    N, arr = map(str, input().split())
    len_num = int(N)
    sixteen = []
    for i in range(len_num):
        sixteen.append(arr[i])
    i = len_num - 1
    alpha_num = ['A', 'B', 'C', 'D', 'E', 'F']
    alpha = [['0000'],['0001'],['0010'],['0011'],['0100'],['0101'],['0110'],['0111'],['1000'],['1001'],['1010'],['1011'],['1100'],['1101'],['1110'],['1111']]
    # 함수를 만들다가 작동이 이상하여 이렇게 먼저 계산해보았다.
    # 다시 함수를 만들어본다!!

    for j in range(len_num):
        for i in range(6):
            if sixteen[j] == alpha_num[i]:
                sixteen[j] = str(10 + i)
    # ['4', '7', '15', '14'] 알파벳들을 바꾸어주면 이렇게 변환된다.

    for i in range(len_num):
        for j in range(len(alpha)):
            if int(sixteen[i]) == j:
                sixteen[i] = alpha[j][0]
                break
                # break를 안걸어주면 왜 그런지 모르겠지만 2가 2진법으로 표시할 때 10으로 표시된다.
                # 그래서 test_case 2개밖에 맞지 않는다. 이유는 모르겠다..
    # ['0100', '0111', '1111', '1110'] 이렇게 표시되어 안의 원소들만 추출해준다.

    print(f'#{test_case}', ''.join(sixteen))

```

함수를 이용한 다른 풀이

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

# 16745.5185
def binary(n):
    global x
    global list_ans

    if x > -1:
        a = n // 2
        b = n % 2
        list_ans[x] = str(b)
        x -= 1
        if a == 0:
            return list_ans
        else:
            binary(a)
    else:
        return list_ans

T = int(input())

for test_case in range(1, T+1):
    N, arr = map(str, input().split())
    len_num = int(N)
    sixteen = []
    for i in range(len_num):
        sixteen.append(arr[i])
    x = 3
    alpha_num = ['A', 'B', 'C', 'D', 'E', 'F']

    for j in range(len_num):
        for i in range(6):
            if sixteen[j] == alpha_num[i]:
                sixteen[j] = str(10 + i)
    # ['4', '7', '15', '14'] 알파벳들을 바꾸어주면 이렇게 변환된다.
    ans = []
    list_ans = ['0', '0', '0', '0']
    for j in range(len_num):
        binary(int(sixteen[j]))
        ans.append(list_ans)
        list_ans = ['0', '0', '0', '0']
        x = 3
    # print(f'#{test_case} {ans}')
    real_ans = []
    for i in range(len_num):
        for j in range(4):
            real_ans.append(ans[i][j])
    print(f'#{test_case}', ''.join(real_ans))
```