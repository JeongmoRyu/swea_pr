# swea_view 1206


```python
for test_case in range(1, 11):
    

    N = int(input())
    building_list = list(map(int, input().split()))
    count = 0
    for a in range(2, N-2):
        compare = [-2, -1, 1, 2]
        near_building = []
        for b in compare:
            near_building.append(building_list[a+b])

        if building_list[a] - max(near_building) > 0:
            count += building_list[a] - max(near_building)

    print(f'#{test_case} {count}')
```

다른 풀이
- built in 함수를 쓰지 않고 연습

```python
import sys
sys.stdin = open("input.txt", "r")

# 여러개의 테스트 케이스가 주어지므로, 각각을 처리합니다.
for test_case in range(1, 11):
    
    N = int(input())
    building_list = list(map(int, input().split()))
    count = 0
    for a in range(2, N-2):
        compare = [-2, -1, 1, 2]
        near_building = []
        for b in compare:
            near_building.append(building_list[a+b])

        for c in range(3, 0, -1):
            for x in range(0, c):
                if near_building[x] > near_building[x+1]:
                    near_building[x], near_building[x+1] = near_building[x+1], near_building[x]

        if building_list[a] - near_building[-1] > 0:
            count += building_list[a] - near_building[-1]

    print(f'#{test_case} {count}')
```


input
too much
버퍼를 만들어서 제거
