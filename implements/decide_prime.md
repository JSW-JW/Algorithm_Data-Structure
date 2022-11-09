# prime number 구하는 코드 모범 코드

```python
def decidePrime(num):
    flag = False
    if num > 1:
       # check for factors
       for i in range(2,num):
           if (num % i) == 0:
               flag = True
               break
           
    # if input number is less than
    # or equal to 1, it is not prime
    else:
       return False
       
    return not flag
      
nums = [1, 2, 3, 4, 5]
for num in nums:
    isPrime = decidePrime(num)
    print('{} is Prime ?: '.format(num), isPrime)
```
