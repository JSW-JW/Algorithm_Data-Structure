# 프로그래머스 카카오 2022 intern 등산코스 정하기
```python
import sys
input = sys.stdin.readline
from collections import deque

def solution(n, paths, gates, summits):
    INF = 10**9
    ans = [-1, 1e9]
    g = [[] for _ in range(n+1)]
    for path in paths:
        i,j,w = path
        g[i].append([j, w])
        g[j].append([i, w])
    dp = [INF] * (n+1)
    summits = set(summits)
    gates = set(gates)
        
    def bfs():
        nonlocal ans
        q = deque([])
        for gt in gates:
            for nxt, w in g[gt]:
                if dp[nxt] > w:
                    q.append((nxt, w))
                    dp[nxt] = w
            
        while q:
            node, w = q.popleft()
            # 산봉우리 라면
            if node in summits:
                if w < ans[1]:
                    ans = [node, w]
                elif w == ans[1]:
                    winner = node if node < ans[0] else ans[0]
                    ans[0] = winner
                continue
            # 출입구 라면
            elif node in gates:
                continue
            # 쉼터 라면
            for nxt, w_nxt in g[node]:
                mx_intensity = max(w, w_nxt)
                if dp[nxt] > mx_intensity:
                    dp[nxt] = mx_intensity
                    q.append((nxt, mx_intensity))
                    
    bfs()
    return ans
```
