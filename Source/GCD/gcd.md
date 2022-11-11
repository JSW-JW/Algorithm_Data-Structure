# how to get GCD(Greatest Common Divisor) using recursion

```python
def gcd(a, b):
  if b == 0:
    return a:
  else:
    return gcd(b, (a % b))
```
