# swea carge dork

**16751. 5202.**

- input

```
3
5
20 23
17 20
23 24
4 14
8 18
10
14 23
2 19
1 22
12 24
21 23
6 15
20 24
1 4
6 15
15 16
15
18 19
2 7
11 15
13 16
23 24
2 14
13 22
20 23
13 19
7 15
5 21
20 24
16 22
17 21
9 24
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N = int(input())
    arr = []
    for _ in range(N):
        arr.append(list(map(int, input().split())))

    for i in range(len(arr) - 1):
        for j in range(len(arr) - i - 1):
            if arr[j][1] > arr[j+1][1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    # print(arr)

    # 문제 풀이 고안 1
    # visited를 만들어 준다.
    # visited에 한 시간을 넣어준다.
    # 나머지 넣을 수 있은 것을 넣어준다.
    # 더 넣을 수 있다면 계속 넣어준다.
    # 안되면 넣어준 원소 즉 화물차의 갯수를 리스트화 해준다.
    # 리스트 최댓값

    # 문제 풀이 고안 2
    # 종료 시간이 빠른 순서로 활동을 정리한다.
    # 그리고 종료보다 빠른 시작 시간을 가지는 활동은 다 제거한다.
    # 반복
    ans = 0
    n = 0
    while len(arr) != 0:
        first_fin = arr[0][1]
        arr.pop(n)
        ans += 1
        while len(arr) > 0 and arr[n][0] < first_fin:
            arr.pop(0)

    print(f'#{test_case} {ans}')

```