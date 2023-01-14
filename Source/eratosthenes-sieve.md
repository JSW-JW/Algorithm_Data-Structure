# 백준 1929 소수 구하기

```python
import sys
input = sys.stdin.readline


def sol(n, mask):
    for i in range(2, n+1):
        if mask[i] == 0: continue
        for j in range(2*i, n+1, i):
            mask[j] = 0
                

m,n = map(int, input().split())
mask = [1] * 1_000_001
mask[1] = 0 #  1은 소수가 아님

sol(n, mask)

for i in range(m, n+1):
    if mask[i] == 1: print(i)
```
