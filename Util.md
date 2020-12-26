```
유클리드 호제법을 이용한 GCD 공식

(a > b 라 가정)
def gcd(a,b):
  return b if a % b == 0 else gcd(b, a%b)
  
  
```
