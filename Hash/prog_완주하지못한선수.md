# 프로그래머스 완주하지 못한 선수
[완주하지 못한 선수](https://school.programmers.co.kr/learn/courses/30/lessons/42576)

```python
from collections import defaultdict

def solution(participant, completion):
    participant.sort()
    completion.sort()
    
    for i in range(len(participant)):
        if i >= len(completion): return participant[i]
        if completion[i] != participant[i]:
            return participant[i]
        
    # O(nlogn + n) = O(nlogn)
    # 연산 횟수: 약 14_100_000 번
```
