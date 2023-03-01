# 프로그래머스 미로 탈출
```python
from collections import deque

def solution(maps):
    n, m = len(maps), len(maps[0])
    for i in range(n):
        for j in range(m):
            if maps[i][j] == 'S':
                s = (i, j)
            if maps[i][j] == 'L':
                l = (i, j)
            if maps[i][j] == 'E':
                e = (i, j)

    def bfs(s, dest): # start dest
        dx, dy = [0, 1, 0, -1], [1, 0, -1, 0]
        v = [[0] * m for _ in range(n)]
        q = deque([])
        q.append((s[0], s[1], 0))
        v[s[0]][s[1]] = 1
        ans = 1e9
        
        while q:
            x, y, c = q.popleft()
            if (x, y) == dest:
                ans = min(ans, c)
            for i in range(4):
                nx, ny = x + dx[i], y + dy[i]
                if not (0 <= nx < n and 0 <= ny < m): continue
                if maps[nx][ny] != 'X' and v[nx][ny] == 0:
                    q.append((nx, ny, c+1))
                    v[nx][ny] = 1
        return ans
    
    ans = 0
    res = bfs(s, l)
    if res == 1e9:
        return -1
    ans += res
    
    res = bfs(l, e)
    if res == 1e9:
        return -1
    ans += res
    
    return ans
```
