# 프로그래머스 혼자 놀기의 달인
```python
from itertools import combinations

def solution(cards):
    N = len(cards)
    cards = [0] + cards
    ans = 0
    
    """
    [1,4,7,8]   <-> [2,5,6] <-> [3]
    [1,4,7,8] 그룹과 [2,5,6] 두 그룹 각각에 해당하는 상자를 하나씩 고르면 답이 된다.
    입력의 크기가 100 이하로 작은 편이다.
    a, b 각 그룹의 시작점에 해당하는 상자 2개를 고르는 모든 경우의 수에 대해 탐색할 수 있다.
    """
    i = 0
    for comb in combinations(range(1, len(cards)), 2):
        i += 1
        a,b = comb # 1, 2
        a_box_cnt, b_box_cnt = 1, 1
        v = [0] * len(cards)
        v[a] = 1
        while v[cards[a]] == 0:
            v[cards[a]] = 1
            a = cards[a]
            a_box_cnt += 1
            
        if a_box_cnt == N: 
            return 0

        v[b] = 1
        while v[cards[b]] == 0:
            v[cards[b]] = 1
            b = cards[b]
            b_box_cnt += 1
        ans = max(ans, a_box_cnt * b_box_cnt)
        
    return ans
```
