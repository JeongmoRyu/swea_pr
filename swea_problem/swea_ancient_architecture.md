# swea_ancient_architecture

9489


![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/905b47ce-332d-40d6-8c4f-b3f7dddc606b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230326%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230326T035239Z&X-Amz-Expires=86400&X-Amz-Signature=cd3142cf7fa9c55cfbfcf0b563b7d81924ec9336c635d943bde34d085ce86835&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- input

```python
3
3 3
0 1 0
0 1 0
0 1 0
3 3
0 1 0
1 1 1
0 0 0
8 8
1 0 0 0 0 0 1 0
1 0 1 1 1 0 1 0
1 0 0 0 0 0 1 0
0 0 0 1 0 0 1 0
0 0 0 1 0 0 1 0
0 1 1 0 0 0 1 0
0 0 0 0 0 0 0 0
0 0 0 0 1 1 1 1
```
- solve
```python
import sys
sys.stdin = open("../input1.txt", "r")

def count(arr):
    mx = 2
    for lst in arr:
        cnt = 0
        for n in lst:
            if n == 1:
                cnt += 1
                if mx < cnt:
                    mx = cnt
            else:
                cnt = 0
    return mx

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    N, M = map(int, input().split())
    arr = [list(map(int, input().split())) for _ in range(N)]
    arr_t = list(map(list, zip(*arr)))

    ans = count(arr)
    t = count(arr_t)
    if ans < t:
        ans = t
    print(f'#{test_case} {ans}')

```