```
global max_value # for comparing values, initialize it as global and use it inside the function.
max_value = -999999
def find_max(A, n):
	global max_value
	if n == 0:
		return max_value
	if A[n-1] > max_value:
		max_value = A[n-1]
	return find_max(A, n-1)
	
A = [200, 1002, 305, 299]
print(find_max(A, 4))
```
