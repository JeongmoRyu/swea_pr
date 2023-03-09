# swea_put_in_color 4836

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/30eca7a1-7ce9-4d21-b188-df156172bc96/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230309%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230309T000610Z&X-Amz-Expires=86400&X-Amz-Signature=ec366e5327ba7eb4b470fd714ca939f97ebc36eef13d0e64e2ccee20aeb6da6b&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- input

```python
3
2
2 2 4 4 1
3 3 6 6 2
3
1 2 3 3 1
3 6 6 8 1
2 3 5 6 2
3
1 4 8 5 1
1 8 3 9 1
3 2 5 8 2
```

- solve

```python
import sys
sys.stdin = open('input.txt', 'r')

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    arr = []
    for x in range(10):
        arr.append([0]*10)

    # 10 * 10 격자에 빨간색 파란색을 칠한다.
    # 빨강색은 1
    # 파랑색은 2
    for _ in range(N):
        Sx, Sy, Ex, Ey, Color = list(map(int, input().split()))
        #시작점과 끝점 그리고 컬러의 색을 입력시켜준다.

        for i in range(10):
            # 10 * 10 격자이므로 범위는 i와 j의 범위는 10으로 잡아준다.
            if Sx <= i <= Ex:
                # 만약 시작점과 끝점을 포함하여 범위 안에 존재하면 color로 잡아준 색의 값을 더해준다.
                for j in range(10):
                    if Sy <= j <= Ey:
                        arr[i][j] = arr[i][j] + Color
    # 전체에서 색의 값을 확인하고
    # 보라색은 파랑색과 빨강색을 더한 값인 3이 되므로 3의 값을 count 해주면 끝이 나게 된다.
    count = 0
    for i in range(10):
        for j in range(10):
            if arr[i][j] == 3:
                count += 1
    print(f'#{test_case} {count}')
```


