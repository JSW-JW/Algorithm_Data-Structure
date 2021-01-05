Source code from code signal (https://app.codesignal.com/interview-practice)


    def largestValuesInTreeRows(t):
        traverseAndLogTree(t, 0)
        return maxes


    def traverseAndLogTree(node, row):
        if not node:
            return

        if len(maxes) < row + 1:
            maxes.append(node.value)

        if maxes[row] < node.value:
            maxes[row] = node.value

        traverseAndLogTree(node.left, row + 1)
        traverseAndLogTree(node.right, row + 1)
    
*One of the way to search Node Tree and the way to solve it can be different depending on their perspectives.*

```
def digitTreeSum(t):
        stack = [(t, 0)]
        res = []
        sum = 0

    while stack:
        v, w = stack.pop()
        w = int(str(w) + str(v.value))
        if v.left or v.right:
            if v.left:
                stack.append((v.left, w))
            if v.right:
                stack.append((v.right, w))
        else:
            sum += w
    return sum
```
*My own code for the first time!*

[프로그래머스 타겟 넘버](https://programmers.co.kr/learn/courses/30/parts/12421)
```
def solution(numbers, target):
    n = len(numbers)
    count = 0
    
    def dfs(depth, ttl):
        if depth == n:
            if ttl == target:
                nonlocal count
                count += 1
        else:
            dfs(depth+1, ttl + numbers[depth])
            dfs(depth+1, ttl - numbers[depth])
    dfs(0, 0)
    return count
```
**recursion**

```
def solution(numbers, target):
    q = [0]
    for n in numbers:
        s = []
        for _ in range(len(q)):
            x = q.pop()
            s.append(x + n)
            s.append(x + n*(-1))
        q = s.copy()
    return q.count(target)
```
**stack**

_itertools의 product에 대하여_ 

**예시를 통해 확실히 감을 익혀보자**

```
from itertools import product
data = ['A', 'B', 'C'] # 데이터 준비
result = list(product(data, repeat= 2)) # 2개를 뽑는 모든 순열 구하기(중복 허용)
print(result)

결과: [('A', 'A'), ('A', 'B'), ('A', 'C'), ('B', 'A'), ('B', 'B'), ('B', 'C'), ('C', 'A'), ('C', 'B'), ('C', 'C')]
```

```
곱집합(Cartesian product) 구하기 - product
이번 강의에서는 iterable으로 곱집합을 구하는 방법을 알아봅니다.

예시) 두 스트링 'ABCD', 'xy' 의 곱집합은 Ax Ay Bx By Cx Cy Dx Dy 입니다.

다른 언어에서는..(또는 이 기능을 모르시는 분은)
보통 사람들은 for 문을 이용해 두 iterable의 원소를 하나씩 곱해갑니다.

iterable1 = 'ABCD'
iterable2 = 'xy'
iterable3 = '1234'

for i in iterable1:
    for j in iterable2:
        for k in iterable3:
            print(i+j+k)
파이썬에서는
itertools.product를 이용하면, for 문을 사용하지 않고도 곱집합을 구할 수 있습니다.

import itertools

iterable1 = 'ABCD'
iterable2 = 'xy'
iterable3 = '1234'
itertools.product(iterable1, iterable2, iterable3)

결과: [('A', 'x', '1'), ('A', 'x', '2'), ('A', 'x', '3'), ('A', 'x', '4'), ('A', 'y', '1'), ('A', 'y', '2'), ('A', 'y', '3'), 
('A', 'y', '4'), ('B', 'x', '1'), ('B', 'x', '2'), ('B', 'x', '3'), ('B', 'x', '4'), ('B', 'y', '1'), ('B', 'y', '2'),
('B', 'y', '3'), ('B', 'y', '4'), ('C', 'x', '1'), ('C', 'x', '2'), ('C', 'x', '3'), ('C', 'x', '4'), ('C', 'y', '1'),
('C', 'y', '2'), ('C', 'y', '3'), ('C', 'y', '4'), ('D', 'x', '1'), ('D', 'x', '2'), ('D', 'x', '3'), ('D', 'x', '4'), 
('D', 'y', '1'), ('D', 'y', '2'), ('D', 'y', '3'), ('D', 'y', '4')]
```

```
from itertools import product

src = ['abc', '123',  'def']
cartesian_product = [''.join(t) for t in product(*src)]
print(cartesian_product)

결과: ['a1d', 'a1e', 'a1f', 'a2d', 'a2e', 'a2f', 'a3d', 'a3e', 'a3f', 'b1d', 'b1e', 'b1f', 'b2d', 'b2e', 'b2f', 'b3d', 'b3e',
'b3f', 'c1d', 'c1e', 'c1f', 'c2d', 'c2e', 'c2f', 'c3d', 'c3e', 'c3f']
```

위와 같은 예시를 통해 감을 익혔으면 위의 '타겟넘버' 문제에 대해 다음과 같은 코드도 작성 가능할 것이다.

```
from itertools import product
def solution(numbers, target):
    l = [(x, -x) for x in numbers]
    s = list(map(sum, product(*l))) // 변수 l을 unpacking 해줌으로써, 튜플 여러개(iterable한 요소)를 product의 인자로 넣어줌.
    return s.count(target)
```


```
# Recursive Python function to solve the tower of hanoi 
  
def TowerOfHanoi(n , source, destination, auxiliary): 
    if n==1: 
        print "Move disk 1 from source",source,"to destination",destination 
        return
    TowerOfHanoi(n-1, source, auxiliary, destination) 
    print "Move disk",n,"from source",source,"to destination",destination 
    TowerOfHanoi(n-1, auxiliary, destination, source) 
          
# Driver code 
n = 4
TowerOfHanoi(n,'A','B','C')  
# A, C, B are the name of rods 
  
# Contributed By Dilip Jain 
```

Tower of Hanoi Phtyon code.
