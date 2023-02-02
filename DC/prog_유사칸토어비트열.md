# 프로그래머스 유사 칸토어 비트열
```python
def solution(n, l, r):
    """
    0 0 0 0 0
    1 1 0 1 1
    
    11011 11011 00000 11011 11011  /  11011 / 1 
    110[11 11011 00000 11]011 11011
    
    1. 유사 칸토어 비트열은 크게 5 등분으로 나눌 수 있다. (3번째 등분은 0 만 있으므로 제외한다)
    2. 나눠진 각 등분은 반복적으로 5 등분으로 나눌 수 있다. 
    3. 비트열의 크기가 5 가 되었을 때 1 의 개수를 계산하여 리턴한다.
    """
    ans = DC(n, l, r)
    return ans

def DC(n, l, r): # n 번째 비트열
    # n-1 번쨰 비트열 의 5 등분으로 나누고 3번쨰 는 제외
    if r - l <= 4:
        one_bit = (r - l) + 1
        if l <= 3 <= r: one_bit -= 1
        return one_bit
    
    ans = 0
    for i in range(1, 6):
        if i == 3: continue
        ran = [5 ** (n-1) * (i-1) + 1, 5 ** (n-1) * i]
        
        l_partial = max(l, ran[0])
        r_partial = min(r, ran[1])
        if l_partial > r_partial: continue
        
        tmp = (5 ** (n-1)) * (i-1)
        nxt_l, nxt_r = l_partial - tmp, r_partial - tmp
        ans += DC(n-1, nxt_l, nxt_r)
    
    return ans
```
