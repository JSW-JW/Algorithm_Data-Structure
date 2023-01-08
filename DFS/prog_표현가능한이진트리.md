# 프로그래머스 표현 가능한 이진트리


[표현 가능한 이진트리](https://school.programmers.co.kr/learn/courses/30/lessons/150367)

```python
def solution(numbers):
    ans = []
    for num in numbers:             # (2^n - 1) 개
        bi = decimalToBinary(num)         # 101010
        n, left = findSquare(bi)          # n = 3
        root = 2**(n-1) -1                # 2^2 -1
        bi = '0' * (left - len(bi)) + bi  # 0101010
        
        representative = dfs(root, n-2, bi)  # left child: index(parent) - 2^(depth-1)
                                            # right child: index(parent) + 2^(depth-1)
            
        if representative: ans.append(1)
        else: ans.append(0)
        
    return ans

def dfs(x, n, s):
    if n == -1: return True
    
    l, r = x - 2**n, x + 2**n
    
    if (s[x] == '0' and s[l] == '1') or (s[x] == '0' and s[r] == '1'):
        return False
        
    res1 = dfs(l, n-1, s)
    res2 = dfs(r, n-1, s)
    
    if res1 and res2: 
        return True
    return False

def findSquare(bi):
    n = 0
    while True:
        if 2**n - 1 >= len(bi): break
        n += 1
        
    return n, 2**n -1

def decimalToBinary(n):
    return "{0:b}".format(int(n))
```
