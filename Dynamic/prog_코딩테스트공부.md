# 프로그래머스 코딩테스트 공부
```python
import sys
input = sys.stdin.readline


def solution(alp, cop, problems):
    """
    (0, 0) -> (10, 11)
    (현재 풀수 있는 문제 + 공부) 중 최선의 옵션을 선택한다. 
    
    (alp, cop, cost)               
    (10, 5)
    
            ... (12,13)
    """
    # dp [i][j] = 알고력 i 코딩력 j 를 얻기 위한 최소 비용
    dp = [[1e9] * 151 for _ in range(151)]
    alp_max = max([problem[0] for problem in problems])
    cop_max = max([problem[1] for problem in problems])
    alp = min(alp, alp_max)
    cop = min(cop, cop_max)
    dp[alp][cop] = 0
    for i in range(alp, alp_max+1):
        for j in range(cop, cop_max+1):
            can_sol = [(problem[2], problem[3], problem[4]) for problem in problems if problem[0] <= i and problem[1] <= j]
            for sol in can_sol:
                nxt_i, nxt_j = i + sol[0], j + sol[1]
                if nxt_i > alp_max: nxt_i = alp_max
                if nxt_j > cop_max: nxt_j = cop_max
                dp[nxt_i][nxt_j] = min(dp[nxt_i][nxt_j], dp[i][j] + sol[2])
            if i+1 <= alp_max: dp[i+1][j] = min(dp[i+1][j], dp[i][j] + 1)
            if j+1 <= cop_max: dp[i][j+1] = min(dp[i][j+1], dp[i][j] + 1)
    
    return dp[alp_max][cop_max]
```
