[프로그래머스 체육복](https://programmers.co.kr/learn/courses/30/lessons/42862/solution_groups?language=python3)
```
def solution(n, lost, reserve):
    lost.sort()
    reserve.sort()
    # 여벌이 있는 학생이 도둑 맞은 경우
    for i in range(len(lost)):
        if lost[i] in reserve:
            reserve.remove(lost[i])
            lost[i] = 0
    
    # 왼쪽부터 그리디 탐색
    for i in range(len(lost)):
        if (lost[i]-1) in reserve:
            reserve.remove(lost[i]-1)
            lost[i] = 0
            continue
        if (lost[i]+1) in reserve:
            reserve.remove(lost[i]+1)
            lost[i] = 0
    
    # 전체 학생 수 - 체육복을 빌려주고 나서도 체육복이 없는 학생 수
    for i in range(len(lost)):
        if lost[i] != 0:
            n -= 1
    return n
```


refactor code

```
def solution(n, lost, reserve):
    _lost = [l for l in lost if l not in reserve]
    _reserve = [r for r in reserve if r not in lost]
    
    for r in _reserve:
        f = r-1
        b = r+1
        if f in _lost:
            _lost.remove(f)
        elif b in _lost:
            _lost.remove(b)
    return n - len(_lost)
```
**위의 코드와 로직은 크게 다르지 않지만, <br> 1. 처음에 예외 케이스를 걸러주는 부분에서 코드 가독성이 좋고** <br>
**2. iterator 변수와 loop 안에서 remove해주는 list의 변수를 다른 것으로 설정하여 iterating 하는 과정에서 오류가 날 가능성이 없음**
