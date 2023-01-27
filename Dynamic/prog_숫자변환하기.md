# 프로그래머스 숫자 변환하기
```python
def solution(x, y, n):
    """
    완전탐색 하지 않고, x 를 y 로 변환하는 경우의 수 ? 모른다
    dp[k] = x 를 k 으로 변환하는데 든 최소 연산 횟수
    1. 점화식 
        dp[k] = min(dp[k-n], dp[k//2], dp[k//3]) + 1
    2. 초기화
        dp 의 모든 값을 1e9 로 초기화 (dp 연산 후에 1e9 로 남아있다면 해당 수는 만들 수 없는 수)
        dp[x] =  0 으로 초기화
    """
    dp = [1e9] * (y+1)
    dp[x] = 0
    
    for i in range(x+1, y+1):
        if i-n >= 0 and dp[i-n] != 1e9:
            dp[i] = dp[i-n] + 1
        if i % 2 == 0 and dp[i // 2] != 1e9:
            dp[i] = min(dp[i], dp[i // 2] + 1)
        if i % 3 == 0 and dp[i // 3] != 1e9:
            dp[i] = min(dp[i], dp[i // 3] + 1)
            
    return dp[y] if dp[y] != 1e9 else -1
```
