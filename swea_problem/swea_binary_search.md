# swea_binary_serach 4839

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b057cd9b-9cef-4a0e-b50f-de3978699c85/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230312%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230312T005934Z&X-Amz-Expires=86400&X-Amz-Signature=209cdacd1202e0d06b1b9eb168921de45e231831529e470d9bcea7fdace757ca&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- input

```python
3
400 300 350
1000 299 578
1000 222 888
```

- solve
```python
import sys
sys.stdin = open("sample_input1.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    P, key_a, key_b = map(int, input().split())
    # 끝 지점과 a, b의 원하는 값을 찾아준다.
    left_a = 1
    right_a = P
    count_a = 0
    # a의 시작점을 준비하고 a 값을 찾기 위해 count를 정해준다.

    while left_a <= right_a:
        center_a = int((left_a + right_a)//2)

        if center_a == key_a:
            count_a += 1
            break
        elif center_a > key_a:
            right_a = center_a
            count_a += 1
        else:
            left_a = center_a
            count_a += 1
    # 이진 탐색을 위한 함수를 while을 통해서 구현한다.
    # b 역시 마찬가지로 수행한다.
    left_b = 1
    count_b = 0
    right_b = P
    while left_b <= right_b:
        center_b = int((left_b + right_b)//2)
        if center_b == key_b:
            count_b += 1
            break
        elif center_b > key_b:
            right_b = center_b
            count_b += 1
        else:
            left_b = center_b
            count_b += 1

    # 교과서에서 적은 count 값을 가진 사람이 이긴다는 것을 알려준다.
    if count_a == count_b:
        print(f'#{test_case} 0')
    elif count_a < count_b:
        print(f'#{test_case} A')
    else:
        print(f'#{test_case} B')
```