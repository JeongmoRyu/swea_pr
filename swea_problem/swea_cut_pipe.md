# swea_cut_pipe
13685

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/eeb95500-87f6-4712-a62e-f54844d6c674/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230327%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230327T022141Z&X-Amz-Expires=86400&X-Amz-Signature=722fe6d8b133c91e34c8d8a44d768b20ce52b219e2b57e8cde2474b3482d27bc&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- input 

```python
2
()(((()())(())()))(())
(((()(()()))(())()))(()())
```

```python
import sys
sys.stdin = open("sample_input.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////
    arr = input()
    ans = 0
    count = 0
    for i in range(len(arr)):
        if arr[i] == '(':
            count += 1
            # ')' 바로 앞의 기호에 따라 레이져 혹은 막대기 의 끝
        else:
            if arr[i-1] == '(':
                count -= 1
                ans += count
            else:
                count -= 1
                ans += 1

    print(f'#{test_case} {ans}')

```