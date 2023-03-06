# swea_new_bus_lane 13994

- input
```
1
3
1 2 5
2 3 10
3 2 9
 
```

- solve
```python
import sys
sys.stdin = open("sample_in.txt", "r")

T = int(input())
# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, T + 1):
    # ///////////////////////////////////////////////////////////////////////////////////

    N = int(input())
    stop_list = [0]
    # for y in range(N):
    #     stop_list{y} = []
    # stop_list1 = []
    # stop_list2 = []
    # stop_list3 = []
    ans = []
    # 라인의 수가 3개 밖에 없다는 것으로 해석하여 나누어서 input을 하였는데
    # runtime error와 오답이 발생하였다.
    # normal, S1, E1 = map(int, input().split())
    # fast, S2, E2 = map(int, input().split())
    # dis, S3, E3 = map(int, input().split())
    # # 주어진 값들을 input 해준다.normal, fast, dis 와 출발지점, 도착지점 모두를
    # 타입 별로 for문을 사용하여 각자 input을 하는 방식으로 변화하였다.
    for x in range(N):
        type, S, E = map(int, input().split())
        if type == 1:
            for a in range(S, E + 1):
                stop_list.append(a)
                # 전구역에 다 멈춘다.
        elif type == 2:
            for b in range(S, E + 1):
                if S % 2 == 0:
                    if b % 2 == 0:
                        stop_list.append(b)
                # 고속 버스의 경우에서는 시작점이 짝수일 경우에는 짝수 번째에서만 멈춘다.
                elif S % 2 == 1:
                    if b % 2 == 1:
                        stop_list.append(b)
                # 고속 버스의 경우에서는 시작점이 홀수일 경우에는 홀수 번째에서만 멈춘다.
        elif type == 3:
            for c in range(S, E + 1):
                if S % 2 == 0:
                    if c % 4 == 0:
                        stop_list.append(c)
                # 광역 버스의 경우에서는 시작점이 짝수 일경우 4의 배수에서 멈춘다.
                elif S % 2 == 1:
                    if c % 3 == 0 and not c % 10 == 0:
                        stop_list.append(c)
                # 광역 버스의 경우에서는 시작점이 홀수 일경우 3의 배수이거나 10의 배수가 아닌 지점에서 멈춘다.
    cnts = [0]*(len(stop_list)+1)

    for y in range(0, len(stop_list)):
        cnts[stop_list[y]] = cnts[stop_list[y]] + 1


    print(f'#{test_case} {max(cnts)}')
    # 그 중 최대 값을 출력한다.
```