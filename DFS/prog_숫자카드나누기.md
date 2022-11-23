# 프로그래머스 숫자 카드 나누기 (reduce 를 이용한 gcd multiple numbers 구현)

```python
from functools import reduce

def solution(arrayA, arrayB):
    answer = 0
    
    gcd_A = reduce(lambda x,y:GCD(x,y), arrayA)
    for i in range(gcd_A, 1, -1):
        if gcd_A % i == 0:
            divisible = False
            for num in arrayB:
                if num % i == 0:
                    divisible = True
                    break
    
        if divisible is False: answer = max(answer, i)
        
    gcd_B = reduce(lambda x,y:GCD(x,y), arrayB)
    for i in range(gcd_B, 1, -1):
        if gcd_B % i == 0:
            divisible = False
            for num in arrayB:
                if num % i == 0:
                    divisible = True
                    break
    
        if divisible is False: answer = max(answer, i)
        
    
        
    return answer



def GCD(a, b):

    if b == 0:
        return a
    else:
        return GCD(b, a % b)
```
