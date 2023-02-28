# swea babygin 16181

input
```python
9
111456
123123
233677
112233
333333
123456
667767
054060
101123
```



```python
#
# import sys
# sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    list_baby = list(map(int, input().split()))
    # 케이스들을 split하여 입력하게 해준다.

    c = [0]*12
    for a in range(len(list_baby)):
        for x in range(6):
            c[list_baby[a] % 10] += 1
            list_baby[a] //= 10
            # 진행방식입니다.
            # c[6] = 1
            # c[5] = 1
            # c[4] = 1
            # c[1] = 1
            # c[1] = 2
            # c[1] = 3
    #6자리 수로부터 각 자리 수를 추출하여 개수를 누적할 리스트
    triple = 0
    count = 0
    i = 0
    while i < 10:
        if c[i] >= 3:
            # triple 조사하고 데이터 삭제(초기화해주는 것 입니다.)
            c[i] -= 3
            triple += 1
            continue
            # 반복문을 돌 때 continue를 만나면 뒷부분을 실행하지 않고 반복문 처음으로 돌아간다.
        if c[i] >= 1 and c[i+1] >= 1 and c[i+2] >= 1:
            # run 조사 후 데이터 삭제(초기화해주는 것 입니다.)
            c[i] -= 1
            c[i+1] -= 1
            c[i+2] -= 1
            count += 1
            continue
        # 수행되었을 떄 i 가 더해진다.
        i += 1
        
    if triple + count == 2:
        print(f'#{test_case} 1')
        # 이후 triple과 run이 두개 다 있을 경우 babygin
    else:
        print(f'#{test_case} 0')
        # 하나만 있거나 둘다 없을 경우 아니기에 0을 print해준다.
   
# run이라는 이름으로 사용할 시 실행할 때 문제가 발생할 수 있다.
    # /////////////////////////////////////////////////////////////////////////////////// 여기에 코드 입력
```