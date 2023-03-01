# swea_flatten 1208

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4350a888-ee6d-46b1-a974-53b8b1a7449c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230301%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230301T234647Z&X-Amz-Expires=86400&X-Amz-Signature=11ec393a6890e87bec444ead6c51e5343fda3216713cd43b25c525d2c6b21600&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

```python
import sys
sys.stdin = open("input.txt", "r")

# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, 11):
    # ///////////////////////////////////////////////////////////////////////////////////
    N = int(input())
    # 이동 가능한 숫자를 입력하세요
    list_box = list(map(int, input().split()))
    # 박스들의 높이들을 분리하여 리스트화하세요

    for a in range(N+1):
        # N을 사용해서 처음 fail이 떳다. test_case 6번의 정답과 1의 차이가 있었다.
        # N-1을 사용하니 test_case 6번과 7번에서 차이가 생겼다.
        # N+1을 사용해보니 되었다.
        # 이유를 찾아보자..
        max_height = max(list_box)
        min_height = min(list_box)
        # 박스들의 최대 최소 값들을 설정해준다.
        # for문 밖에 두었다가 max와 min을 계속 설정해주어야해서 안쪽으로 잡아두었습니다.
        max_index = list_box.index(max(list_box))
        min_index = list_box.index(min(list_box))
        # 최대값의 위치와 최소값의 위치를 찾는다.
        # for문 밖에 두었다가 max와 min을 계속 설정해주어야해서 안쪽으로 잡아두었습니다.
        list_box[max_index] -= 1
        list_box[min_index] += 1
        # list_box의 최대 최소 위치를 찾아주고 그 값에서
        # 최대 높이를 가진 위치의 높이 값에서 1을 빼주고
        # 최소 높이를 가진 위치의 높이 값에 1을 더해준다.

    # 최대 높이와 최소 높이의 차이를 구해준다.
    print(f'#{test_case} {max_height - min_height}')
```

```
이런게 여러개가 있습니다.
834
42 68 35 1 70 25 79 59 63 65 6 46 82 28 62 92 96 43 28 37 92 5 3 54 93 83 22 17 19 96 48 27 72 39 70 13 68 100 36 95 4 12 23 34 74 65 42 12 54 69 48 45 63 58 38 60 24 42 30 79 17 36 91 43 89 7 41 43 65 49 47 6 91 30 71 51 7 2 94 49 30 24 85 55 57 41 67 77 32 9 45 40 27 24 38 39 19 83 30 42


```