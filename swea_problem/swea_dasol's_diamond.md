# swea_dasol’s_diamond 4751

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d9c3f1ca-b218-4b86-9112-eb785cbf05c5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230317%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230317T224817Z&X-Amz-Expires=86400&X-Amz-Signature=8f3ae59331b8c7875bc972b48afdb3871af1b825e6759b1456f42f5081773285&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- input

```jsx
2
D
APPLE
```

- solve

```python
import sys
sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////

    word = input().split()

    # print(word[0])
    # print(len(word[0]))
    len_word = len(word[0])
    arr = [['.'] * (4*(len_word)+1) for _ in range(5)]

    for i in range(4*(len_word)+1):
        if i%4 == 2:
            arr[0][i] = '#'
            arr[4][i] = '#'
            for j in range(len_word):
                arr[2][4*j + 2] = word[0][j]
        if i%2 == 1:
            arr[1][i] = '#'
            arr[3][i] = '#'
        if i%4 == 0:
            arr[2][i] = '#'
    print("".join(arr[0]))
    print("".join(arr[1]))
    print("".join(arr[2]))
    print("".join(arr[3]))
    print("".join(arr[4]))
```