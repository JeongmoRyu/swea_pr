# swea killing fly 2001

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/66bd0f82-8a9f-4f50-a031-fcbfcf168d7a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230310%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230310T005216Z&X-Amz-Expires=86400&X-Amz-Signature=a29360603f17a867fdfd034122a86372c6b8ae424f1bbed5e3a8508d2ae51e1c&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)


- input
```jsx
10
5 2
1 3 3 6 7
8 13 9 12 8
4 16 11 12 6
2 4 1 23 2
9 13 4 7 3
6 3
29 21 26 9 5 8
21 19 8 0 21 19
9 24 2 11 4 24
19 29 1 0 21 19
10 29 6 18 4 3
29 11 15 3 3 29
...
```
- solve
```python
#import sys
#sys.stdin = open("input.txt", "r")

for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N, M = map(int, input().split())
    arr = [list(map(int, input().split())) for _ in range(N)]
    fly = 0
    for a in range(N-M+1):
        for b in range(N-M+1):
            flystick = 0

            for i in range(M):
                #
                for j in range(M):
                    flystick += arr[a+i][b+j]
            if fly < flystick:
                fly = flystick
    
    print(f'#{test_case} {fly}'
```