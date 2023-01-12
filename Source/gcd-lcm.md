# 백준 2609 최대공약수 최소공배수

```python
a,b = map(int, input().split())

def gcd(a, b):
    if a == 0 or b == 0:
        return a+b
        
    a %= b
    return gcd(b, a)
        
gcd = gcd(a, b)
lcm = int((a*b)/gcd)
    
print(gcd)
print(lcm)
```
