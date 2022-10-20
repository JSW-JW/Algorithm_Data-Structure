```
import sys

input = sys.stdin.readline
# 입력 받는 시간을 줄이기 위함. (입력을 여러번 받는 문제의 경우, 시간초과가 날 우려가 있음)

N = int(input())
S = input()

ADR = ['A','B','C']
BRN = ['B','A','B','C']
GOR = ['C','C','A','A','B','B']

A = 0
B = 0
C = 0

for i in range(N):
    a = i % len(ADR)
    b = i % len(BRN)
    c = i % len(GOR)
    
    if S[i] == ADR[a]:
        A += 1
    if S[i] == BRN[b]:
        B += 1
    if S[i] == GOR[c]:
        C += 1
        
l = [A, B, C]
indices = [index for index, item in enumerate(l) if item == max(l)]

print(max(l))
for index in indices:
    if index == 0:
        print("Adrian")
    if index == 1:
        print("Bruno")
    if index == 2:
        print("Goran")
    # 조건문을 사용하지 않고, indices 선언부에서 list comprehension 을 통해 튜플이나 딕셔너리에 넣었으면 더 깔끔했을 것.
```
