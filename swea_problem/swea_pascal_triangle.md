# swea_pascal_triangle 2005

- input
```
1
4
```

- solve

```python
import sys
sys.stdin = open('input.txt.', 'r')

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    # 리스트를 만들어 주고 임시로 저장할 arr를 만들어준다.
    number_list = []
    arr = []
    # number_list = [0]*N
    # arr = [0] * N
    # 를 만들어서 i가 1일때 첫 글자와 마지막 글자에 1을 넣어주었지만
    # 한줄씩 밀려서 파스칼 삼각형이 완성이되었다.
    print(f'#{test_case}')
    # output에 따라서 test_case를 따로 빼준다.
    for i in range(N):
        number_list.append(1)
        arr.append(1)
        if i < 2:
            pass
        # 시작 2번째까지는 사이클에 포함되지 않기 때문에
        else:
            for j in range(1, len(number_list) - 1):
                # number[j] = number[i] + number[i+1]
                arr[j] = number_list[j-1] + number_list[j]
        for j in range(len(number_list)):
            number_list[j] = arr[j]
        # 임시 arr리스트의 값들을 다시 number_list의 값에 넣어준다.
        print(*number_list)
    # arr.append(number)
```

- 다른 풀이

    - 프린트를 미리 뽑아주는 방식을 사용해도 된다.


```python
import sys
sys.stdin = open('input.txt', 'r')

T = int(input())
for test_case in range(1, 11):
		print(f'#{test_case}')
    N = int(input())
    temp = []
    print(1)
    for i in range(N-1):
        for j in range(N-1):
            result = [1]
            result.append(temp[j] + temp[j + 1])
        result.append(1)
        print(*result)
        temp = result
```