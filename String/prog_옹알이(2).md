프로그래머스 옹알이 (문자열 조작 문제)

```python
def solution(babbling):
    # "aya", "ye", "woo", "ma"
    answer = 0
    matching = ["aya", "ye", "woo", "ma"]
    for i in range(len(babbling)):
        word = babbling[i]
        prev = ""
        s = ""
        for j in range(len(word)):
            s += word[j]
            if s in matching and s != prev:
                prev = s
                s = ""
                babbling[i] = word[j+1:]
                
    for bab in babbling:
        if len(bab) == 0: answer += 1
    return answer
```

```python
def solution(babbling):
    answer = 0
    segment = ["aya", "ye", "woo", "ma"]

    for babble in babbling:
        index = 0
        recent = ""

        while index < len(babble):

            if babble[index:index + 3] in segment and babble[index:index + 3] != recent:
                recent = babble[index:index + 3]
                index += 3
                continue

            if babble[index:index + 2] in segment and babble[index:index + 2] != recent:
                recent = babble[index:index + 2]
                index += 2
                continue

            break

        if index >= len(babble):
            answer += 1


    return answer
```
