# 프로그래머스 폰켓몬
```python
from collections import defaultdict

def solution(nums):
    """
    N = len(nums) // 2
    N 만큼 폰켓몬을 선택 하는데,
    최대한 많은 종류의 폰켓몬을 가지는 종류 수를 리턴
    k = 연구실의 총 포켓몬 종류 수
    if N // 2 > k:
        k 를 리턴
    else:
        N 를 리턴
    """
    N = len(nums) // 2
    d = defaultdict(int)
    for num in nums:
        d[num] = 1
        
    k = len(d.keys())
    if N > k:
        return k
    else:
        return N
```
