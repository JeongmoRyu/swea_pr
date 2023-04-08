# swea subtree

16528 5174

- input

```python
3
5 1
2 1 2 5 1 6 5 3 6 4 
5 1
2 6 6 4 6 5 4 1 5 3 
10 5
7 6 7 4 6 9 4 11 9 5 11 8 5 3 5 2 8 1 8 10

```
- solve

```python
import sys
sys.stdin = open('sample_input (1).txt', 'r')

def count_node(tree, n):
    global count
    if n != 0:
        count += 1
        #왼쪽
        count_node(tree, tree[n][0])
        #오른쪽
        count_node(tree, tree[n][1])
    return count

T = int(input())
for test_case in range(1, T +1):
    E, N = map(int, input().split())
    arr = list(map(int, input().split()))

    # print(arr)
    # print(E)
    # print(N)
    tree = [[0 for _ in range(3)] for _ in range(E + 2)]

    for i in range(E):
        parent, child = arr[i*2], arr[i*2 + 1]
        if tree[parent][0] == 0:
            tree[parent][0]= child
        else:
            tree[parent][1] = child

        tree[child][2] = parent

    # print(tree)

    count = 0
    print(f'#{test_case} {count_node(tree, N)}')

```