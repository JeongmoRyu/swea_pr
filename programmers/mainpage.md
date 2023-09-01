# mainpage

```python
def solution(wallpaper):
    sharp = []
    for i in range(len(wallpaper)):
        for j in range(len(wallpaper[0])):
            if wallpaper[i][j] != '.':
                sharp.append((i, j))

    mn_h = len(wallpaper) + 1
    mx_h = 0
    mn_w = len(wallpaper[0]) + 1
    mx_w = 0
    for i in range(len(sharp)):
        if sharp[i][0] < mn_h:
            mn_h = sharp[i][0]
        if sharp[i][0] > mx_h:
            mx_h = sharp[i][0]
        if sharp[i][1] < mn_w:
            mn_w = sharp[i][1]
        if sharp[i][1] > mx_w:
            mx_w = sharp[i][1]

    answer = [mn_h, mn_w, mx_h + 1, mx_w + 1]
    return answer
```
