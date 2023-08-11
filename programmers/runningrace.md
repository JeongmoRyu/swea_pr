# runningrace

```python
def solution(players, callings):
    for i in range(len(callings)):
        num = players.index(callings[i])
        players.pop(num)
        players.insert(num - 1, callings[i])
    return players
```

시간초가가 나오기 때문에 index를 찾아서 숫자를 바꿔주는 것을 생각해야한다.

```python
def solution(players, callings):
    
    dictionary = {}
    
    for idx, player in enumerate(players):
        dictionary[player]=idx
    for player in callings:
        target=dictionary.get(player)
        dictionary[players[target-1]] += 1
        dictionary[player] -= 1
        players[target-1],players[target]=players[target],players[target-1]
    return players
```