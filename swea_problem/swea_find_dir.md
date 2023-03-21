# swea find dir 1219

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/61a83754-4edd-45c2-9ef2-dc63447200d5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230321%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230321T001619Z&X-Amz-Expires=86400&X-Amz-Signature=0be55032b225f88c5968473f51edca77557b835c9ea941f0bc782b4d12b3ca20&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)


![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7785116c-5ca9-4a3a-af08-5764621fa7f7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230321%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230321T001637Z&X-Amz-Expires=86400&X-Amz-Signature=f8b1d7c5d5c38b32c7ecaa700e26afba19baf6be0e7b1d69092a91858aebabc9&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)


- input

```python
1 16
0 1 0 2 1 4 1 3 4 8 4 3 2 9 2 5 5 6 5 7 7 99 7 9 9 8 9 10 6 10 3 7
2 159
0 4 0 10 1 4 1 10 2 11 2 8 3 13 4 8 4 11 5 10 5 8 6 10 6 11 7 8 7 15 8 14 9 10 9 20 10 14 10 17 11 21 12 21 13 14 13 17 14 20 15 22 16 22 16 20 17 19 18 28 18 29 19 27 20 29 21 31 21 30 22 24 22 30 23 24 23 26 24 27 25 31 26 31 26 37 27 34 27 30 28 38 28 30 29 32 30 38 30 32 31 35 31 36 32 34 32 37 33 40 33 44 34 44 35 39 35 46 36 38 36 41 37 40 38 40 38 49 39 41 39 44 40 45 41 44 41 50 42 44 42 51 43 45 43 52 44 45 44 52 45 48 45 52 46 47 46 55 47 48 47 58 48 53 49 55 50 59 50 60 51 57 51 60 52 60 52 63 53 57 53 62 54 62 54 65 55 62 56 58 57 66 58 64 58 61 59 69 60 62 61 63 62 68 62 64 63 66 64 68 64 71 65 75 65 67 66 75 66 73 67 71 67 72 68 72 68 70 69 72 70 71 70 80 71 80 72 81 72 83 73 77 73 75 74 83 74 78 75 81 75 85 76 79 76 82 77 86 77 87 78 86 78 81 79 89 80 84 80 86 81 83 81 88 82 87 82 86 83 86 83 94 84 94 84 88 85 95 86 91 86 97 87 93 88 92 88 90 89 97 89 92 90 99 91 95 92 96 92 97 94 95 95 97 95 99 96 97

 이런게 10개 ㅎㅎ

```

- solve

```python
import sys
sys.stdin = open('input.txt', 'r')

def depth_first_search(ver):
    global count
    # 함수 호출되면 거기 방문한 것
    visited[ver] = 1
    # 작은 숫자부터 세기
    # print(ver, end='-')

    for next in range(1, 100):
        # 인접하고 미방문이면
        if adjM[ver][next] == 1 and visited[next] == 0:
            if ver == 99:
                count = 1
                return True
            #     count += 1
            #     break
            # 다음 함수 호출
            depth_first_search(next)

    return

for test_case in range(1, 11):
    count = 0
    X, num = map(int, input().split())
    adjM = [[0] * (100) for _ in range(100)]
    arr = list(map(int, input().split()))
    for i in range(num):
        v1, v2 = arr[i * 2], arr[i * 2 + 1]
        adjM[v1][v2] = 1
        # adjM[v2][v1] = 1
        # 한방향이기 때문에
    visited = [0 for _ in range(100)]

    # depth_first_search(0)
    depth_first_search(0)
    if visited[-1] == 1:
        count = 1

    # print(list_ans)
    # for i in range(len(list_ans)):
    #     if 99 in list_ans:
    #         count = 1
    print(f'#{test_case} {count}')

```

- 조금 더 정리한 풀이 방식

```python
import sys
sys.stdin = open('input.txt', 'r')

def depth_first_search(now, visited):
		if visited[99] == 1:
        return
    visited[now] = 1
    for next in range(100):
        # 연결되어 있고 방문한적 없다.
        if connections[now][next] == 1 and visited[next] == 0:
            depth_first_search(next, visited)

for test_case in range(1, 11):
    N, edges = map(int, input().split())
    raw_data = list(map(int, input().split()))

    # 0 ~ 99 까지
    visited = [0 for _ in range(100)]

    connections = [[0 for _ in range(100)] for _ in range(100)]

    for i in range(edges):
        connections[raw_data[i*2]][raw_data[i*2 + 1]] = 1

    depth_first_search(0, visited)

    print(f'#{test_case} {visited[99]}')

```