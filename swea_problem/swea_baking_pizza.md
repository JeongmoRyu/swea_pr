# swea baking pizza

16524


- input

```python
3
3 5 
7 2 6 5 3
5 10
5 9 3 9 9 2 5 8 7 1
5 10
20 4 5 7 3 15 2 1 2 2
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')
T = int(input())

for test_case in range(1, T + 1):
    N, M = map(int, input().split())
    arr = list(map(int, input().split()))
    # list_num = []
    # for i, word in enumerate(arr):
    #     list_num.append((i+1, word))

    cheeze = []
    for i in range(M):
        cheeze.append([arr[i], i])
    print(cheeze)
    tunnel = []
    for i in range(N):
        tunnel.append(cheeze[i])
        # cheeze.pop(0)

    print(tunnel)
    num = 0
    while len(tunnel) > 1:
        tunnel[0][0] //= 2

        if tunnel[0][0] == 0:
            if N + num < M:
                # 첫 피자를 뒤로 보내준다. (회전)
                tunnel.pop(0)
                tunnel.append(cheeze[N + num])
                num += 1
            else:
                tunnel.pop(0)
            # 치즈 녹은 피자를 빼준다.
        else:
            tunnel.append(tunnel.pop(0))
        # 치즈가 안녹은 피자 하나를 빼준다.

    print(f'#{test_case} {tunnel[0][1] + 1}')
```

- 다른 풀이

```python
t = int(input())
for tc in range(1,t+1):
    # 화덕의 크기 N, 피자의 개수 M
    N, M = map(int, input().split())
    # 각 피자의 치즈의 양을 입력 받음
    num_list = list(map(int,input().split()))
    # 피자의 접시 번호를 리스트에 할당,
    # 초기값 0을 미리 넣어준다.
    dish_list = [0]

    # queue 를 생성, 초기값을 미리 넣어준다.
    que = [num_list[0]]
    # 저장된 원소 중 마지막 자리를 rear 변수에 할당,
    # queue에 미리 넣어줬으므로 초기값은 0으로 설정
    rear = 0
    i = 1

    # queue 가 완전히 비워질 때까지 반복한다.
    while que:
        # rear가 N-1이면 queue가 꽉 찼으므로
        # 화덕 한 바퀴 돌리고 처음 들어간 피자의 치즈 양을 체크한다(check 변수에 할당)
        # 이 때 접시 번호 리스트도 pop 하여 확인한다.
        # check // 2 한 값이 0보다 크다면 다시 queue 의 마지막에 append 해주고
        # 접시 번호도 같이 append 해준다.
        if rear == N - 1:
            check = que.pop(0)
            dish_num = dish_list.pop(0)
            if check // 2:
                que.append(check // 2)
                dish_list.append(dish_num)
            # check // 2 값이 0이라면 그 피자를 빼주므로 queue, 접시 번호 리스트에서
            # 각각 pop한다.
            # 그리고 저장된 원소 중 마지막 자리를 의미하는 rear 에서 1을 빼준다.
            else:
                # 이 조건은 i 가 M 에 도달할 때, 즉 더 이상 넣을 피자가 없다면
                # 아래의 else 문으로 가지 않도록 하기 위한 조건이다.
                if i == M:
                    rear += 1
                rear -= 1
        # rear 가 N - 1 이 아니라면, 즉 queue가 아직 덜 찼다면,
        # rear 에 1을 더해주고, queue에 피자의 치즈 양을 append 해주고
        # 그에 해당하는 인덱스 i를 접시 번호 리스트에 append 해준다.
        # 그리고 다음 인덱스를 살펴보기 위해 i += 1 해줌
        else:
            rear += 1
            que.append(num_list[i])
            dish_list.append(i)
            i += 1
    # 출력하고자 하는 접시 번호는 인덱스 + 1 이므로
    print(f'#{tc} {dish_num + 1}')

```