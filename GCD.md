```
def gcd_mod(a,b):
  while a!=0 and b!=0:
    if a > b:
      a = a % b
    else:
      b = b % a
  return a + b
```

```
def gcd_sub(a,b):
  while a!=0 and b!=0:
    if a > b:
      a = a - b
    else:
      b = b - a
  return a + b
```


```
def gcd_rec(a,b):
  if a == 0 or b == 0:
    return a + b
    
  if a > b:
    a = a % b
  else:
    b =  b % a
  gcd_rec(a,b)
```
