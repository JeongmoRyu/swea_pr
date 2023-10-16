# 코딩테스트 공부

- 초기의 `알고력`을 나타내는 `alp`와 초기의 `코딩력`을 나타내는 `cop`가 입력으로 주어집니다.
    - 0 ≤ `alp`,`cop` ≤ 150
- 1 ≤ `problems`의 길이 ≤ 100
- `problems`의 원소는 [`alp_req`, `cop_req`, `alp_rwd`, `cop_rwd`, `cost`]의 형태로 이루어져 있습니다.
- `alp_req`는 문제를 푸는데 필요한 `알고력`입니다.
    - 0 ≤ `alp_req` ≤ 150
- `cop_req`는 문제를 푸는데 필요한 `코딩력`입니다.
    - 0 ≤ `cop_req` ≤ 150
- `alp_rwd`는 문제를 풀었을 때 증가하는 `알고력`입니다.
    - 0 ≤ `alp_rwd` ≤ 30
- `cop_rwd`는 문제를 풀었을 때 증가하는 `코딩력`입니다.
    - 0 ≤ `cop_rwd` ≤ 30
- `cost`는 문제를 푸는데 드는 시간입니다.
    - 1 ≤ `cost` ≤ 100

**정확성 테스트 케이스 제한사항**

- 0 ≤ `alp`,`cop` ≤ 20
- 1 ≤ `problems`의 길이 ≤ 6
    - 0 ≤ `alp_req`,`cop_req` ≤ 20
    - 0 ≤ `alp_rwd`,`cop_rwd` ≤ 5
    - 1 ≤ `cost` ≤ 10

**효율성 테스트 케이스 제한사항**

- 주어진 조건 외 추가 제한사항 없습니다.

---

### 입출력 예

| alp | cop | problems | result |
| --- | --- | --- | --- |
| 10 | 10 | [[10,15,2,1,2],[20,20,3,3,4]] | 15 |
| 0 | 0 | [[0,0,2,1,2],[4,5,3,1,2],[4,11,4,0,2],[10,4,0,4,2]] | 13 |

```python
import heapq

def solution(alp, cop, problems):
#     [[10, 15, 2, 1, 2], [20, 20, 3, 3, 4]]
#     alg필요, cop필요, alg올라간정도, cod올라간 정도, 비용
#     10 10
# 1. 시간을 늘려서 알고, 코딩 늘리거나
    problems += [[0,0,1,0,1]]
    problems += [[0,0,0,1,1]]
# 2. 문제를 풀어서 알고나 코딩을 늘린다.
# 3. 모든 문제를 해결할 수 있는 최단시간을 구한다.
    def solve(timeCost, key):
        if key not in dp or timeCost < dp[key]:
            dp[key] = timeCost  
            heapq.heappush(queue, (timeCost, key))
    dp = {(alp, cop): 0}
    algomax = max(i[0] for i in problems)
    codmax = max(i[1] for i in problems)
    queue = [(0, (alp, cop))]
    while queue[0][1][0] < algomax or queue[0][1][1] < codmax:
        ct, (cal, cco) = heapq.heappop(queue)
        for alreq, coreq, alrwd, corwd, cost in problems:
            if cal >= alreq and cco >= coreq:
                solve(ct+cost, (min(cal+alrwd, 150), min(cco+corwd, 150)))
    return queue[0][0]
```
