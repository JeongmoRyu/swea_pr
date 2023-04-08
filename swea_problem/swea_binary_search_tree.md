# swea binary search tree

16529 5176
- input

```python
3
6
8
15
```

```python

import sys
sys.stdin = open('sample_input (1).txt', 'r')

T = int(input())

# 우리가 넣을 순서를 생각하보면 L V R
# 완전 이중 트리임을 알고 있으니 인덱스만 받는다.
def tree_make(i):
    global num
    # N을 넘어가지 않는 숫자까지 tree_make 를 돌린다.
    if i <= N:
				# L V R
        # 왼쪽 아이는 현재 2배
        tree_make(i*2)
        # num 1일때 재귀로 2를 돌린다.
        # print(arr)
        # 값 넣고 num 증가시킨다.
        arr[i] = num
        num += 1
        # 우측 아이는 2배 + 1
        tree_make(i*2 + 1)
        # print(arr)
        # 넣고 증가하였을 돌리고 num이 올라가면

        # [0, 0, 0, 0, 1, 0, 0] # [0, 1, 1, 0, 1, 0, 0]
        # [0, 0, 2, 0, 1, 3, 0] # [0, 1, 1, 0, 1, 3, 0]
        # [0, 0, 2, 0, 1, 3, 0] # [0, 1, 1, 0, 1, 3, 0]
        # [0, 4, 2, 0, 1, 3, 5] # [0, 1, 1, 5, 1, 3, 5]
        # [0, 4, 2, 6, 1, 3, 5] # [0, 1, 1, 5, 1, 3, 5]
        # [0, 4, 2, 6, 1, 3, 5] # [0, 1, 1, 5, 1, 3, 5]
        # 이런 식으로 num이 올라가면서 트리를 채워주게 된다.

for test_case in range(1, T + 1):
    N = int(input())

    # head = N // 2 + 1
    # 루트의 값은 직관적으로 절반 값보다 1큰 숫자가 된다.
    # 이러면 test_case 10개 중 4개가 맞는다.

    # 넣어줄 트리를 만든다. 최대값이 들어갈 수 있는 0의 갯수
    arr = [0 for i in range(N + 1)]
    #  1부터시작하는 들어갈 숫자
    num = 1
    tree_make(1)

    # arr이 앞에 0이 있기 때문에
    # 위치점은 +1 지점으로
    # 시작점은 arr[1]이 헤드가 된다.
    # N//2 점은 arr[N//2]
    print(f'#{test_case} {arr[1]} {arr[N//2]}')

```

다른풀이

```python

import sys
sys.stdin = open('input.txt', 'r')

def in_order(tree, node):
    global count
    # 자식이 존재할때
    if node != 0 :
        # L-V-R
        in_order(tree, tree[node][0])
        tree[node].append(count)
        count += 1
        in_order(tree, tree[node][1])

T = int(input())

for test_case in range(1, T + 1):
    N = int(input())

    tree = [[0 for _ in range(3)] for _ in range(N + 1)]
    # 완전 이진 트리는 부모자식 관계가 인덱스로 쉽게 구현됨
    for i in range(1, N + 1):
        # 내 왼쪽
        tree[i][0] = 2 * i
        if 2*i > N:
            tree[i][0] = 0
        # 내 오른쪽
        tree[i][1] = 2 * i + 1
        if 2*i + 1 > N:
            tree[i][1] = 0
        # 부모
        tree[i][2] = i // 2
    count = 1
    in_order(tree, 1)
    print(f'#{test_case} {tree[1][-1]} {tree[N//2][-1]}')
```