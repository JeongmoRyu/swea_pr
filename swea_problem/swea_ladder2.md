
## swea_ladder2 1211

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/47b047f7-3e10-4691-a02b-0dce527a8965/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230312%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230312T010453Z&X-Amz-Expires=86400&X-Amz-Signature=89fd2d7d7043b77a68975838af3c4d1c33cc7cb8146294a9ddcd2f288de44683&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

```python
import sys
sys.stdin = open("../input.txt", "r")

# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, 11):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    arr = [[0] + list(map(int, input().split())) + [0] for _ in range(100)]

    mn = 100*100
    for sj in range(1, 101):
        si = 0
        if arr[si][sj]!=1:
            continue
        # dj(-1, 1, 0)
        # 갈 수 있는 방향성으로 좌, 우, 밑
        # 좌, 우를 우선적으로 고려하여 갈 수 있으면 보낸 후
        # 가지 못할 경우에 밑으로 내려가게 된다.

        count, dj = 0, 0
        ci, cj = si, sj
        # 높이의 범위를 기준으로 while문으로 반복문을 생성한다.
        while ci<99:
            count += 1
            if dj == 0:
                if arr[ci][cj-1] == 1:
                    # 좌측으로 이동
                    dj = -1
                    cj -= 1
                elif arr[ci][cj + 1] ==1:
                    # 우측으로 이동
                    dj = 1
                    cj += 1
                else:
                    ci += 1
            else:
                if arr[ci][cj+dj] == 1:
                    # 진행방향에서 직진할 수 있는 경우

                    cj += dj
                else:
                    # 진행방향이 끝이난 경우 밑으로 이동
                    dj = 0
                    ci += 1
        # 정답을 구하기 위해 끝 경계선을 생기게 하여 1의 숫자를 제거해준다.
        if mn >= count:
            mn, ans = count, sj - 1

    print(f'#{N} {ans}')

```