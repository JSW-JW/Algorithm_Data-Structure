# 프로그래머스 숫자 변환하기
```python
from collections import deque

def solution(x, y, n):
    """
    x 에서 시작하여 (x+n, x*2, x*3) 인 수에 대해 bfs 를 진행한다
    visited = [0] * (y+1)
    """
    visited = [0] * (y+1)
    q = deque([])
    q.append(x)
    # visit 을 이용하여 연산 횟수를 계산하고 있기 떄문에 
    # 시작 지점은 방문 체크를 0 으로 그대로 두어야 한다.
    
    if x == y: return 0
    while q:
        a = q.popleft()
        for nxt in [a + n, a * 2, a * 3]:
            if nxt == y: return visited[a] + 1
            if nxt <= y and visited[nxt] == 0:
                visited[nxt] = visited[a] + 1
                q.append(nxt)
    return -1
```
