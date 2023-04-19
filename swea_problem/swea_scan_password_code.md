# swea scan password code
1243

저번 2진 암호코드 문제에서

업그레이드한 버전

![Untitled](https://swexpertacademy.com/main/common/fileDownload.do?downloadType=CKEditorImages&fileId=AV2XbdgaDf4BBASl)

![Untitled](https://swexpertacademy.com/main/common/fileDownload.do?downloadType=CKEditorImages&fileId=AV2Xbg2KDf8BBASl)

input - 16진수를 2진수로 바꾸고 바꾼 2진수를 암호로 해석하여 판별

```
테스트 케이스	 N * M	암호코드 가로 길이	암호코드 개수
그룹      1	  100 * 26	    56	          1
그룹      2	  200 * 50	  56 ~ 112	      2
그룹      3 	500 * 126	  56 ~ 280	      5
그룹      4 	1000 * 250	제한 없음	    제한 없음
그룹      5 	2000 * 500	제한 없음	    제한 없음
```

- 풀이과정

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())

# 16진수 -> 2진수 dictionary
hex_to_bin = {
    '0': [0, 0, 0, 0],
    '1': [0, 0, 0, 1],
    '2': [0, 0, 1, 0],
    '3': [0, 0, 1, 1],
    '4': [0, 1, 0, 0],
    '5': [0, 1, 0, 1],
    '6': [0, 1, 1, 0],
    '7': [0, 1, 1, 1],
    '8': [1, 0, 0, 0],
    '9': [1, 0, 0, 1],
    'A': [1, 0, 1, 0],
    'B': [1, 0, 1, 1],
    'C': [1, 1, 0, 0],
    'D': [1, 1, 0, 1],
    'E': [1, 1, 1, 0],
    'F': [1, 1, 1, 1],
}
    # 앞쪽 0을 생략한 암호 코드
passcode_dict = {
    (2, 1, 1): 0,
    (2, 2, 1): 1,
    (1, 2, 2): 2,
    (4, 1, 1): 3,
    (1, 3, 2): 4,
    (2, 3, 1): 5,
    (1, 1, 4): 6,
    (3, 1, 2): 7,
    (2, 1, 3): 8,
    (1, 1, 2): 9
}

def code_scanner(width, height, code):
    answer = 0
    # code의 높이만큼 검증
    # 위쪽 줄을 확인해야해서 range 활용
    for row in range(height):
        # idx는 한줄에서 지금 확인중인 글자의 인덱스
        idx = width * 4 - 1
        # 암호코드 8자리 최소길이 == 56, 그떄의 암호코드의 시작과 끝 인덱스 == 0부터 55
        while idx > 54:
            # 1을 만나면 검증 시작
            if code[row][idx] == 1 and code[row - 1][idx] == 0:
                # 여기서 password 초기화를 한다
                password = []
                # if 내부에서 8글자를 다 찾을 예정
                for _ in range(8):
                    # (0)101 == (ci - ) c2 - c3 - c4 (각각 0과 1이 몇번 등장했는지에 대하여)
                    c2 = c3 = c4 = 0

                    # 다음 코드까지 진행 앞이 다 0일 수 있기 때문에 먼저 확인해준다.
                    # 이전 코드의 1번째 0
                    while code[row][idx] == 0:
                        idx -= 1
                    # 각각의 while은 숫자가 변하는 시점에 종료한다.
                    # 이번 코드의 4번째부터 2번째까지 진행
                    while code[row][idx] == 1:
                        idx -= 1
                        c4 += 1
                    while code[row][idx] == 0:
                        idx -= 1
                        c3 += 1
                    while code[row][idx] == 1:
                        idx -= 1
                        c2 += 1

                    ratio = min(c2, c3, c4)
                    password.append(passcode_dict[(c2 // ratio, c3 // ratio, c4 // ratio)])
                # for문 종료 (8자리 코드 완성)

                even_digit_sum = password[0] + password[2] + password[4] + password[6]
                odd_digit_sum = password[1] + password[3] + password[5] + password[7]
                if (odd_digit_sum*3 + even_digit_sum)%10 == 0:
                    answer += (odd_digit_sum + even_digit_sum)

            # 검증하지 않아도 앞으로 가야한다.
            idx -= 1
    return answer

for test_case in range(1, T+1):
    N, M = map(int, input().split())
    arr = [[] for _ in range(N)]
    for i in range(N):
        temp = input()
        for j in range(M):
            arr[i] += hex_to_bin[temp[j]]

    print(f'#{test_case} {code_scanner(M, N, arr)}')

```

practice 

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, 1+1):
    N, M = map(int, input().split())

    arr = [list(input()) for _ in range(M)]

    alpha_num = ['A', 'B', 'C', 'D', 'E', 'F']
    for i in range(N):
        for j in range(M):
            for k in range(6):
                if arr[i][j] == alpha_num[k]:
                    arr[i][j] = str(10 + k)
    ans = []
    # print(arr)
    list_num = ['1','2','3','4','5','6','7','8','9','10','11','12','13','14','15']
    binary_num = ['0000','0001','0010','0011','0100','0101','0110','0111','1000','1001','1010','1011','1100','1101','1110','1111']

    code = []
    for i in range(N):
        for j in range(M):
            if arr[i][j] in list_num:
                code.append((i, j))

    x = code[0][0]
    y = code[0][1]
    line_code = []
    for j in range(code[0][1], M):
        if arr[code[0][0]][j] != '0':
            line_code.append(arr[code[0][0]][j])

    print(line_code)
    for i in range(len(line_code)):
        for j in range(16):
            if int(line_code[i]) == j:
                line_code[i] = binary_num[j]
    print(line_code)
    temp = ''.join(line_code)

    list_temp = ['0' for _ in range(4)]

    for i in range(len(temp)):
        list_temp.append(temp[i])
    for _ in range(4):
        list_temp.append('0')
    while len(list_temp)%56 != 0:
        if list_temp[-1] == '0':
            list_temp.pop(-1)
        if list_temp[0] == '0':
            list_temp.pop(0)

    print(''.join(list_temp))

    # for i in range(N):
    #     for j in range()
    # 아이디어 추가

```