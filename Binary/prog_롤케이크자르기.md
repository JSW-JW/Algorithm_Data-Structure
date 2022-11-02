# 프로그래머스 롤케이크 자르기

### 시간초과
```python
import sys
sys.setrecursionlimit(10**6)
partials = []

def solution(topping):
    answer = 0
    result = recur_binary(topping, 0, len(topping)-1)
    if result is False:
        answer = 0
    else:
        left, right = checkRange(topping, partials[0])
        answer = right - left - 1
    return answer

def checkRange(topping, std):
    left, right = std, std
    while True:
        left -= 1
        a = len(set(topping[:left]))
        b = len(set(topping[left:]))
        if a != b: break
    while True:
        right += 1
        a = len(set(topping[:right]))
        b = len(set(topping[right:]))
        if a != b: break
    return (left, right)

def recur_binary(topping, start, end):
    if end - start <= 1: return False
    mid = (start + end) // 2
    left = len(set(topping[:mid]))
    right = len(set(topping[mid:]))
    if left > right: return recur_binary(topping, start, mid)
    elif left < right: return recur_binary(topping, mid, end)
    else: 
        partials.append(mid)
        return True
```
