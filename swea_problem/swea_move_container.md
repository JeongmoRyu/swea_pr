# move container

**16750. 5201**

- input

```
3
3 2
1 5 3
8 3
5 10
2 12 13 11 18
17 4 7 20 3 9 7 9 20 5
10 12
10 13 14 6 19 11 5 20 11 14
5 18 17 8 9 17 18 4 1 16 15 13
```

- solve

```python
import sys
sys.stdin = open('sample_input.txt', 'r')

T = int(input())
for test_case in range(1, T+1):
    N, M = map(int, input().split())
    container = list(map(int, input().split()))
    truck = list(map(int, input().split()))
		# input을 받는다.

		# 정답을 위한 옮겨진 number을 만들어준다.
    number = 0
		# 함수를 만들어준다.
    def solve(start):
        global container
        global truck
        global number
				# container의 최고값이 담을 수 있는 트럭의 최고값보다 작은 경우
				# max를 사용하기 위해서 리스트가 존재해야한다.
        if len(container) != 0 and len(truck) != 0 and max(container) <= max(truck):
						# 옮겨진 컨터이너의 양을 더해준다.
						# 옮긴 container를 빼주고 truck을 빼준다.
						# 처음 문제를 생각했을 때에는 트럭에 가득가득 채워서 보낼려고 했는데 문제에서 트럭 한대에 컨테이너 하나만 들어간다고 했기에 
						# A = [1, 2, 3, 4]
						# A.pop(A.index(max(A)))
						# A[A.index(max(A))] -= 2
						# print(A)
						# [1, 2, 3]
						# [1, 2, 1]
            number += max(container)
            container.pop(container.index(max(container)))
            truck.pop(truck.index(max(truck)))
            solve(start)
				# container의 최고값이 담을 수 있는 트럭의 최고값보다 큰 경우
        elif len(container) != 0 and len(truck) != 0 and max(container) > max(truck):
						# 어짜피 담을 수 있는 트럭이 없기에 그냥 제외시키고 다음 재귀로 넘어간다.
            container.pop(container.index(max(container)))
            solve(start)
				# 더 담을 컨테이너가 없다면
        elif len(container) == 0:
            return
		# 함수 실행
    solve(0)
		# 정답을 도출해준다.
    print(f'#{test_case} {number}')

```

- 

- 다른 풀이 방법
    - 내림차림순 혹은 오름차순으로 정렬해서 pop
    - len(container)혹은 len(truck) ≠ 0 을 쓰는 것이 아니라 while 에서의 Falsy를 활용하여 조건들을 걸러내는 것도 좋은 방법이었던 것 같습니다.