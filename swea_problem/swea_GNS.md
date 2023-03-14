# swea_GNS 1221


- input

```
#1 7041
SVN FOR ZRO NIN FOR EGT EGT TWO FOR FIV FIV ONE SVN ONE ONE FIV TWO SVN SIX ONE FOR TWO THR TWO TWO ONE SIX EGT FIV SVN SIX ONE EGT NIN TWO SVN NIN FIV FOR THR ONE TWO THR THR FOR ONE ONE THR EGT SVN FOR TWO SVN SVN NIN THR ONE NIN EGT SIX FIV ZRO TWO EGT SIX ZRO TWO FOR EGT SIX FIV ZRO NIN ZRO ZRO SIX ONE THR EGT NIN THR FOR FOR SIX ZRO SIX SIX ONE...
```

- 그냥 무대뽀로 풀어버린것

```python
T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    dash, num = map(str, input().split())
    arr = list(map(str, input().split()))
    number = int(num)
    # 주어진 값들을 받아준다.
    # enumerate 함수를 통해서 영어 숫자를 숫자로 변환한다.
    for index, value in enumerate(arr):
        if value == 'ZRO':
            arr[index] = 0
    for index, value in enumerate(arr):
        if value == 'ONE':
            arr[index] = 1
    for index, value in enumerate(arr):
        if value == 'TWO':
            arr[index] = 2
    for index, value in enumerate(arr):
        if value == 'THR':
            arr[index] = 3
    for index, value in enumerate(arr):
        if value == 'FOR':
            arr[index] = 4
    for index, value in enumerate(arr):
        if value == 'FIV':
            arr[index] = 5
    for index, value in enumerate(arr):
        if value == 'SIX':
            arr[index] = 6
    for index, value in enumerate(arr):
        if value == 'SVN':
            arr[index] = 7
    for index, value in enumerate(arr):
        if value == 'EGT':
            arr[index] = 8
    for index, value in enumerate(arr):
        if value == 'NIN':
            arr[index] = 9
    # 변환한 후 순서대로 정렬한다.
    new_arr = sorted(arr)
    # 다시 원래대로 정렬하면 끝
    for index, value in enumerate(new_arr):
        if value == 0:
            new_arr[index] = 'ZRO'
    for index, value in enumerate(new_arr):
        if value == 1:
            new_arr[index] = 'ONE'
    for index, value in enumerate(new_arr):
        if value == 2:
            new_arr[index] = 'TWO'
    for index, value in enumerate(new_arr):
        if value == 3:
            new_arr[index] = 'THR'
    for index, value in enumerate(new_arr):
        if value == 4:
            new_arr[index] = 'FOR'
    for index, value in enumerate(new_arr):
        if value == 5:
            new_arr[index] = 'FIV'
    for index, value in enumerate(new_arr):
        if value == 6:
            new_arr[index] = 'SIX'
    for index, value in enumerate(new_arr):
        if value == 7:
            new_arr[index] = 'SVN'
    for index, value in enumerate(new_arr):
        if value == 8:
            new_arr[index] = 'EGT'
    for index, value in enumerate(new_arr):
        if value == 9:
            new_arr[index] = 'NIN'

    # # ZRO < ONE < TWO < THR < FOR < FIV < SIX < SVN < EGT < NIN
    # print(Y)
    print(dash)
    print(*new_arr)
```

- solve 2

```python
# 다른풀이법
# 리스트로 착실하게 하나씩
import sys
sys.stdin = open("../GNS_test_input.txt", "r")
T = int(input())
for test_case in range(1, T + 1):
# 리스트로 착실하게 하나씩
    _, str_len = input().split()
    # 리스트형
    number_words = input().split()
    number_list = ["ZRO", "ONE", "TWO", "THR", "FOR", "FIV", "SIX", "SVN", "EGT", "NIN"]
    
    result = ''
    
    for number in number_list:
        for word in number_words:
            if number == word:
                result += word + ""
    
    print(f'#{test_case}')
    print(result)
```

- solve 3

```python
# 다른풀이법
 # dictionary 활용

import sys
sys.stdin = open("../GNS_test_input.txt", "r")
T = int(input())
for test_case in range(1, T + 1):
    # dictionary 활용
    _, str_len = input().split()
    # 리스트형
    numbers = input().split()
    
    sorted_numbers = []
    sorted_words = []
    
    str_to_number = {
        'ZRO' : 0,
        'ONE' : 1,
        'TWO' : 2,
        'THR' : 3,
        'FOR' : 4,
        'FIV' : 5,
        'SIX' : 6, 
        'SVN' : 7,
        'EGT' : 8,
        'NIN' : 9,
    }
    number_list = ["ZRO", "ONE", "TWO", "THR", "FOR", "FIV", "SIX", "SVN", "EGT", "NIN"]

    for number in numbers:
        sorted_numbers.append(str_to_number.get(number))
    
    sorted_numbers.sort()
    
    for number in sorted_words:
        sorted_words.append(number_list[number])
    print(f'{test_case} \n {" ".join(sorted_words)}')
```