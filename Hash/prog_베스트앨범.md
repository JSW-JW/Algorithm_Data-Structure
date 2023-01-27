# 프로그래머스 베스트 앨범
```python
from collections import defaultdict

def solution(genres, plays):
    """
    d = {"pop": (3100, [4, 1]), "classic": (1450, [3, 0])}
    
    각 클래식 별로 기록된 곡의 고유 번호를 정렬할 때,
    1차 정렬: 곡의 플레이 횟수가 높은 순서로 (내림차순 정렬)
    2차 정렬: [곡의 플레이 횟수가 같다면] 고유 번호가 낮은 노래 순서로 (오름차순 정렬)
    
    # 장르에 속한 곡이 하나라면, 하나의 곡만 수록
    """
    ans = []
    c = defaultdict(lambda : [0, list()])
    for idx, val in enumerate(plays):
        c[genres[idx]][0] += val
        c[genres[idx]][1].append(idx)
          
    sg = sorted(c.items(), key=lambda x: x[1][0], reverse=True)
    for item in sg:
        item[1][1] = sorted(item[1][1], key=lambda x: (-plays[x], x))
        if len(item[1][1]) < 2: 
            ans.append(item[1][1][0])
        else:
            for j in range(2):
                ans.append(item[1][1][j])
    
    
    return ans
```
