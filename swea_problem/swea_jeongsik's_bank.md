# swea_jeongsik's_bank

4366

- input

```python
1
1010
212
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

# python 이 제공하는 int 함수를 이용한다.
# int('aaaa', b)
# 'aaaa'를 b진수로 변환하는 방법

T = int(input())
for test_case in range(1, T+1):
    second = input()
    third = input()
    third_number = ['0', '1', '2']
    secondary_num = []
    for i in range(len(second)):
        if second[i] == '0':
            temp = second[:i] + '1' + second[i+1:]
            secondary_num.append(int(temp, 2))
        else:
            temp = second[:i] + '0' + second[i+1:]
            secondary_num.append(int(temp, 2))
    for i in range(len(third)):
        for j in third_number:
            if third[i] != j:
                temp = third[:i] + j + third[i+1:]
                if int(temp, 3) in secondary_num:
                    print(f'#{test_case} {int(temp,3)}')
```