# 프로그래머스 디펜스 게임
```python
from heapq import heappush, heappop, heappushpop

def solution(n, k, enemy):
    """
    1. 일단 병사를 소모할 수 있을 떄까지 라운드를 진행한다.
    2. 진행한 라운드 중 현재 라운드 적의 수보다 더 많이 소모한 라운드가 있다면
        해당 라운드에 "무적권" 을 사용한 것으로 번복한다.
    3. "무적권" 을 통해 복구된 병사 수가 있다면, 또 라운드가 진행 가능할 떄까지
        병사를 소모한다.
    """
    ans = 0
    heap = []
    for i, e in enumerate(enemy):
        if n >= e:
            n -= e
            # 최대힙
            heappush(heap, -e)
        else:
            if k: 
                k -= 1
								#  (push 하고 나서 가장 작은 값을 pop 한다. 
								push 와 pop 을 따로 하는 연산에 비해 속도가 더 빠르다)
                M = -heappushpop(heap, -e)
                if M > e:
                    n += (M - e)
            else:
                 return ans
        ans = i + 1
            
    return len(enemy)
```
