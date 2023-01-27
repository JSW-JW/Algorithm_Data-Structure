# 프로그래머스 무인도 여행
```python
from collections import deque

def bfs(x, y, v, g):
    dx = [0, 1, 0, -1]
    dy = [1, 0, -1, 0]
    N, M = len(v), len(v[0])
    q = deque([])
    day = int(g[x][y])
    q.append((x, y))
    v[x][y] = 1
    
    while q:
        x, y = q.popleft()
        for i in range(4):
            nx, ny = x + dx[i], y + dy[i]
            if (nx < 0 or nx >= N) or (ny < 0 or ny >= M): continue
            if v[nx][ny] == 1 or g[nx][ny] == 'X': continue
            q.append((nx, ny))
            v[nx][ny] = 1
            day += int(g[nx][ny])
            
    return day
            
        

def solution(maps):
    """
    1. 각 무인도 마다 -> BFS 호출 -> R
    2. 방문 여부 v 리스트
    3. delta 상하좌우
    4. 각 섬에 머무를 수 있는 날짜를 오름차순으로 배열에 담아 리턴 
    """
    ans = []
    v = [[0] * len(maps[0]) for _ in range(len(maps))]
    for i in range(len(maps)):
        for j in range(len(maps[0])):
            if v[i][j] == 0 and maps[i][j] != 'X':
                day = bfs(i, j, v, maps)
                ans.append(day)
            
    if not ans: ans.append(-1)
    return sorted(ans)
```
