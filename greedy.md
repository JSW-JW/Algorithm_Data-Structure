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
