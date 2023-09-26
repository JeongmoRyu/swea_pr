# delivery service(택배배달과 수거하기)

- input

| cap | n | deliveries | pickups | result |
| --- | --- | --- | --- | --- |
| 4 | 5 | [1, 0, 3, 1, 2] | [0, 3, 0, 4, 0] | 16 |
| 2 | 7 | [1, 0, 2, 0, 1, 0, 2] | [0, 2, 0, 1, 0, 2, 0] | 30 |


![image](https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/7ce63a07-3abd-40a1-87cc-c1f664393aa0/%E1%84%8C%E1%85%A2%E1%84%92%E1%85%A1%E1%86%AF%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%90%E1%85%A2%E1%86%A8%E1%84%87%E1%85%A2%20%E1%84%89%E1%85%A1%E1%86%BC%E1%84%8C%E1%85%A1.png)

- solve

```python
def solution(cap, n, deliveries, pickups):
    answer = 0
    while deliveries and not deliveries[-1]:
        deliveries.pop()
    while pickups and not pickups[-1]:
        pickups.pop()
    while deliveries or pickups:
        answer += 2 * max(len(deliveries), len(pickups))

        deliver_left = pickup_left = cap
        while deliveries:
            if deliveries[-1] <= deliver_left:
                deliver_left -= deliveries[-1]
                deliveries.pop()
            else:
                deliveries[-1] -= deliver_left
                break
        while pickups:
            if pickups[-1] <= pickup_left:
                pickup_left -= pickups[-1]
                pickups.pop()
            else:
                pickups[-1] -= pickup_left
                break

    return answer
```
