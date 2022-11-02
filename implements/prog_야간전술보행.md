# 프로그래머스 야간전술보행 (lv.2) 

```python
def solution(distance, scope, times):
    answer = 0
    z = list(zip(scope, times))
    z.sort(key=lambda x: x[0][0])
    # [([4, 6], [2, 4]), ([7, 8], [2, 2]), ([11, 10], [3, 3])]
    for i in range(len(z)):
        caught, pos = checkWorking(i, z)
        if caught is True:
            answer = pos
            return answer
        if caught is False and i == len(z)-1:
            answer = distance
        
    return answer

def checkWorking(i, z):
    s = min(z[i][0][0], z[i][0][1])
    e = max(z[i][0][0], z[i][0][1])
    w,r = z[i][1][0], z[i][1][1]
    cycle = w+r
    mul = s // cycle
    cur = mul * cycle
    while True:
        if cur == s:
            return [True, cur+1]
        cur += w
        if cur < s:
            cur += r
            if cur >= e:
                return [False, None]
            elif s <= cur < e:
                return [True, cur+1]
        elif s <= cur <= e:
            return [True, s]
        else:
            return [True, s]
```

```python
def solution(distance, scope, times):
    answer = distance
    for i in range(len(scope)):
        if scope[i][0] > scope[i][1]:
            scope[i][0], scope[i][1] = scope[i][1], scope[i][0]
        for j in range(scope[i][0],scope[i][1]+1):
            if (j-1) % sum(times[i]) < times[i][0]:
                answer = min(answer,j)
    return answer
```
