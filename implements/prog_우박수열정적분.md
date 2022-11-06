# 프로그래머스 우박수열 정적분

```python
def solution(k, ranges):
    l = getCollatzSequence(k)
    result = []
    for range in ranges:
        start_off, end_off = range[0], range[1]
        start, end = start_off, len(l) - 1 + end_off
        if start > end:
            result.append(-1.0)
        elif start == end:
            result.append(0.0)
        else:
            di = 0
            while start < end:
                di += (l[start][1] + l[start+1][1]) * 1 / 2
                start += 1
            result.append(di)
            
    return result


def getCollatzSequence(k):
    l = []
    x = 0
    l.append((x, k))
    while k > 1:
        if k % 2 == 0:
            k //= 2
        else:
            k = (3*k) + 1
        l.append((x, k))
        x += 1
        
    return l
```
