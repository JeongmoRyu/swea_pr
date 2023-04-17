# swea binary num2
16746 5186

- input

```python
2개를 추가해서 더해주었다.
testcase의 2개 오류로 인하여
5
0.625
0.1
0.125
0.01
0.001
```

```python
T = int(input())

for test_case in range(1, T+1):
    N = float(input())
    # 실수 값으로 받아준다.
    x = 1/2
    y = 13

    answer = []
    while N and y != 0:
        a = int(N//x)
        N = N % x
        x /= 2
        y -= 1
        answer += str(a)

    if y == 0:
# 원래 answer의 길이가 12개가 넘어버리면 overflow 출력을 했지만
# 다른 수들도 13개로 그쳐져 y가 한단계 더 가면 문제 발생으로 변경하였다.
        print(f'#{test_case} overflow')
    else:
        print(f'#{test_case}', ''.join(answer))
```