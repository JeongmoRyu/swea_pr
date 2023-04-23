# russia flag

4613

![image](https://blog.kakaocdn.net/dn/X51q3/btqCHwAUfzr/x7caKffGLBi5kwDbRr7Le0/img.png)

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdaqe1P%2FbtqCD8VxPsI%2FUooitWlnKYG7dYD62qmxt0%2Fimg.png)

```
2
4 5
WRWRW
BWRWB
WRWRW
RWBWR
6 14
WWWWWWWWWWWWWW
WWRRWWBBBBBBWW
WRRRWWWBWWWWRB
WWBWBWWWBWRRRR
WBWBBWWWBBWRRW
WWWWWWWWWWWWWW
```

```python
T = int(input())
for test_case in range(1, T+1):
    N, M = map(int, input().split())
    arr = [list(str(input())) for _ in range(N)]
    change = []
    for row in arr:
        # 바꿔야해 줄 숫자들이기에
        colorx_w = M - row.count('W')
        colorx_b = M - row.count('B')
        colorx_r = M - row.count('R')
        change.append([colorx_w, colorx_b, colorx_r])
    # print(change)

    # 다바꾸는 것이 2500이라 큰 수로 값을 정했다.
    answer = 2501

    # color_w와 color_b 두가지 숫자를 먼저 정한다.
    # color_w,color_r은 0부터, color_b는 최소 1
    for colorx_w in range(0, N - 2):
        for colorx_b in range(1, N - 1 - colorx_w):
            colorx_r = N - colorx_w - colorx_b - 2

            # 정해진 라인 수 만큼 자신의 색깔로 바꾸는 카운트를 세어준다.
            # 첫번째 줄과 마지막 줄은 제외한다.
            count = 0
            for i in range(colorx_w):
                count += change[1:-1][i][0]
            for j in range(colorx_w, colorx_w + colorx_b):
                count += change[1:-1][j][1]
            for k in range(colorx_w + colorx_b, colorx_w + colorx_b + colorx_r):
                count += change[1:-1][k][2]
            # 최솟값을 찾고
            answer = min(answer, count)

    # 최소값을 구하고 맨윗줄과 맨아랫줄도 바꿔준다.
    # 그리고 바꾼 값을 더해준다.
    answer += change[0][0] + change[-1][2]

    print(f'#{test_case} {answer}')
```