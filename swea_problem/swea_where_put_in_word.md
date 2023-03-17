# swea_where_put_in_word 1979

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2b979c8a-075e-4cb5-b0f5-c9c1bae4f19b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230317%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230317T001003Z&X-Amz-Expires=86400&X-Amz-Signature=654d5fe24f165bc2be3daaa478614262c8c6c05773ccbbe96d1137b725bf0d6d&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- input
```
3
5 3
0 0 1 1 1
1 1 1 1 0
0 0 1 0 0
0 1 1 1 1
1 1 1 0 1
5 3
1 0 0 1 0
1 1 0 1 1
1 0 1 1 1
0 1 1 0 1
0 1 1 1 0 
8 3
1 1 0 1 0 1 1 1
0 1 0 1 0 0 0 1
1 1 1 0 0 1 0 1
0 1 0 1 0 1 1 1
0 0 0 1 0 1 0 1
1 1 1 1 1 1 0 0
0 1 0 0 0 1 0 1
1 1 1 0 1 1 1 1 
```

- solve

```python
import sys
sys.stdin = open("../input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N, K = map(int, input().split())
    ans = 0
    # 정답이 되는 ans를 만들어준다.
    # 문제를 풀면서 값을 초기화 시켜주는 ans와 count의 위치에 따라 정답이 많이 달라졌다.
    # 꾸준한 확인을 하자
    # N의 값이 5 <= N <= 15
    arr = []
    for _ in range(N):
        arr.append(list(map(int, input().split())))
    # arr[i][j] == arr[i][j+1] and arr[i][j+1] == arr[i][j+2] and not arr[i][j+2] == arr[i][j+3]
    # 생각을 해보자

    # 가로가 3개인 경우
    # 3개가 되는 count를 만들어준다.
    for i in range(N):
        for j in range(N-K+1):
            count1 = 0
            #초기화 필요
    # 행 세로 열 가로
    # 열 가로에서 j 부터 시작해서 j+l 까지 칸마다 숫자를 더해준다.
            for l in range(j, j+K):
                if arr[i][l] == 1:
                    count1 += 1

            if count1 == K:
            # K 갯수를 채웠을 경우 옆에 있으면 정답 갯수를 늘리지 않는다.
            #
                if j - 1 >= 0 and arr[i][j-1]:
                    continue
                if j+K < N and arr[i][j+K]:
                    continue
                ans += 1

    # 세로가 3개인 경우
    # 세로는 가로랑 i j 위치만 변화시키고 나머지는 유사하다.
    for i in range(N-K+1):
        for j in range(N):
            count2 = 0
            for l in range(i, i+K):
                if arr[l][j] == 1:
                    count2 += 1
            if count2 == K:
                if i - 1 >= 0 and arr[i-1][j]:
                    continue
                if i+K < N and arr[i+K][j]:
                    continue
                ans += 1

    print(f'#{test_case} {ans}')
```

- 다른풀이

```python
import sys
sys.stdin = open("input.txt", "r")

def count(arr):
    ans = 0
    for lst in arr:
        cnt =0
        for n in lst:
            if n ==1:
                cnt += 1
            else:
                if cnt == K:
                    ans += 1
                cnt = 0
    return ans

T = int(input())
for test_case in range(1, T + 1):
    N, K = map(int, input().split())
    arr = [list(map(int, input().split())) + [0] for _ in range(N)] + [[0]*(N+1)]

    arr_t = list(map(list,zip(*arr)))
    print(f'#{test_case} {ans}')
```