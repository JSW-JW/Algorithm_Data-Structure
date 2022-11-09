# prime number 구하는 코드 모범 코드

```python
def decidePrime(num):
  flag = False
  # prime numbers are greater than 1
  if num > 1:
      for i in range(2, num):
          if (num % i) == 0:
              flag = True
              break

  if flag:
      return False
  else:
      return True
```
