# swea best prize

1244

![image](https://user-images.githubusercontent.com/44769544/87408492-80b60900-c5fe-11ea-8132-3311f4894f86.png)
![image](https://user-images.githubusercontent.com/44769544/87408557-99262380-c5fe-11ea-9c1b-b9b531fb8d6b.png)

![image](https://user-images.githubusercontent.com/44769544/87408659-c07cf080-c5fe-11ea-98f7-697508f72e9a.png)

- input

```
10
123 1
2737 1
757148 1
78466 2
32888 2
777770 5
436659 2
431159 7
112233 3
456789 10
```

- solve

```python
import sys
sys.stdin = open('input (1).txt', 'r')

# 1244

# 문제 풀이 생각
# 만약 count 가 짝수일때 sort_num랑 같다면 정답으로 프린트
# 다시 변환하게 되어도 어짜피 동일 값으로 나오게 된다.
# 홀수라면 마지막 두개를 바꾼 값이 그나마 제일 큰 값이 되기에 끝만 바꾼 값이 된다.

def solve(idx, a):
    global result
    if a == count:
        result = max(int(''.join(num)), result)
        return
    for i in range(idx, len(num)):
        # 처음 자리 부터 하나씩 정해준다.
        for j in range(i + 1, len(num)):
            # 첫자리를 제외하고 그 다음부터 자리가 크다면 한번 교환해준다.
            if num[i] <= num[j]:
                num[i], num[j] = num[j], num[i]
                # 그다음 다시 값을 한번 더 해준다음 재실행
                solve(i, a + 1)
                num[i], num[j] = num[j], num[i]
    if result == 0 and a < count:
        # 홀수라면 마지막 두개를 바꾼 값이 그나마 제일 큰 값이 되기에 끝만 바꾼 값이 된다.
        binary = (count - a) % 2
        if binary == 1:
            num[-1], num[-2] = num[-2], num[-1]
        solve(idx, count)

T = int(input())
for test_case in range(1, T+1):
    int_num, count = map(int, input().split())
    num = list(str(int_num))

    result = 0
    solve(0, 0)

    print(f'#{test_case} {result}')
```