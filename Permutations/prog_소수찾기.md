# 프로그래머스 소수 찾기 (brute force, permutations)

```python
from itertools import permutations


def solution(numbers):
    answer = 0
    checked = [0] * 10000000 
    for i in range(1, len(numbers) + 1):
        nums = list(permutations(numbers, i))
        for num in nums:
            t = ''
            for n in num:
                t += n
            t = int(t)
            if checked[t] == 0:
                isPrime = checkPrime(t)
                checked[t] = 1
                if isPrime is True: answer += 1
    return answer

def checkPrime(number):
    if number == 0 or number == 1: return False
    if number == 2: return True
    isPrime = True
    for i in range(2, (number // 2) + 1):
        if number % i == 0: 
            isPrime = False
            break
    return isPrime
```
