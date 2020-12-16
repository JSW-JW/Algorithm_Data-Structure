import collections

def solution(participant, completion):
    answer = collections.Counter(participant) - collections.Counter(completion)
    return list(answer.keys())[0]


https://programmers.co.kr/learn/courses/30/lessons/42577 프로그래머스 전화번호 목록

```
def solution(phone_book):
    answer = True
    phone_book.sort()
    
    for i in range(len(phone_book) - 1):
        for j in range(i+1, len(phone_book)):
            if phone_book[j].find(phone_book[i]) == 0:
                answer = False
                return answer
    return answer
```

