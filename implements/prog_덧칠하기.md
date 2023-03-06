# 프로그래머스 [덧칠하기](https://school.programmers.co.kr/learn/courses/30/lessons/161989)
```python
def solution(n, m, section):
    """
    1 [2] [3] 4 5 [6] 7 8 
    """
    wall = [i for i in range(n+1)]
    d = set(section)
    if m == 1:
        return len(section)
    mn, mx = min(section), max(section)
    ans = 0
    for i in range(mn, mx+1, m):
        cur = wall[i:i+m]
        should = False
        for sec in cur:
            if sec in d:
                should = True
                break
        if should:
            ans += 1
    return ans
```
