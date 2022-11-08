# 프로그래머스 연속 부분수열 합의 갯수

### 단순 for 문을 이용한 모든 경우의 수 더할 경우 시간 초과
```python
def solution(elements):
    result = set()
    dp = [[0] * len(elements) for _ in range(len(elements))]
    for item in elements: result.add(item)
    
    el = len(elements)
    for i in range(2, el):
        # 길이가 i인 부분 수열 조회
        dp[i][0] = sum(elements[0:i])
        result.add(dp[i][0])
        for j in range(1, el):
            if j+i-1 < el:
                dp[i][j] = dp[i][j-1] - elements[j-1] + elements[j+i-1]
            else:
                dp[i][j] = dp[i][j-1] - elements[j-1] + elements[j+i-1 - el]
            result.add(dp[i][j])
    return len(result) + 1
```
