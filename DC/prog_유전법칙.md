# 프로그래머스 유전법칙 (pccp 모의고사 - 분할 정복 문제)
```python
def solution(queries):
    def DC(n, p):
        if n == 1:
            return 'Rr'
        
        if p <= 4 ** (n-2):
            return 'RR'
        elif 4 ** (n-2) < p <= 2 * 4 ** (n-2):
            return DC(n-1, p - 4 ** (n-2))
        elif 2 * 4 ** (n-2) < p <= 3 * 4 ** (n-2):
            return DC(n-1, p - 2 * 4 ** (n-2))
        else:
            return 'rr'
        
    ans = []
    for n,p in queries:
        ans.append(DC(n, p))
    return ans
```
