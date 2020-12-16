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

https://programmers.co.kr/learn/courses/30/parts/12077 프로그래머스 베스트 앨범
```
def solution(genres, plays):
    res = []
    prev = set(res)
    genre_set = set(genres)

    while prev != genre_set:  
        max_genre = get_max_genre(genres, plays, prev)
        
        prev.add(max_genre)

        greater_plays = -10
        max_count = 0
        
        while max_count < 2:
            for i, genre in enumerate(genres):
                if genre == max_genre and plays[i] != -1 and max_count < 2:
                    if greater_plays == plays[i]:
                        pass
                    else:
                        greater_plays=max(greater_plays, plays[i])
            
            for i in range(len(plays)):
                if plays[i] == greater_plays:
                    res.append(i)
                    plays[i] = -1
            greater_plays = -10
            max_count += 1
            
    return res
    
        


def get_max_genre(genres, plays, prev):
    genre_plays = {}

    for i, genre in enumerate(genres):
        if genre not in genre_plays:
            genre_plays[genre] = plays[i]
        else:
            genre_plays[genre] += plays[i]
    max_val = -1
    for key in genre_plays:
        max_val = max(max_val, genre_plays[key])
    for key in genre_plays:
        if genre_plays[key] == max_val:
            return key
```

reviewed code.

```
from collections import defaultdict
from operator import itemgetter
def solution(genres, plays):
    genre_play_dict = defaultdict(int)
    for genre, play in zip(genres, plays):
        genre_play_dict[genre] += play
    
    genre_rank = [genre for genre, play in sorted(genre_play_dict.items(),
                                                  key=itemgetter(1), reverse=True)]
    
    final_dict = defaultdict(lambda: [])
    for i, genre_play_tuple in enumerate(zip(genres, plays)):
        final_dict[genre_play_tuple[0]].append((genre_play_tuple[1], i))
    
    # {"classic": [(500, 0), (150, 2), (800, 3)], "pop": [(600, 1), (2500, 4)]}
    res = []
    for genre in genre_rank:
        sorted_list = [j for i, j in sorted(final_dict[genre], reverse=True)]
        if len(sorted_list) > 1:
            res.append(sorted_list[0])
            res.append(sorted_list[1])
        else:
            res.append(sorted_list[0])
    
    return res
```
(87.7점) 예외 케이스 찾아서 refactor 하기


https://app.codesignal.com/interview-practice/topics/hash-tables Code Signal Hash Table(GroupingDishes)
```
from collections import defaultdict
def groupingDishes(dishes):
    ingr_dict = defaultdict(lambda: [])
    for lst in dishes:
        for j in range(1, len(lst)):
            ingr_dict[lst[j]].append(lst[0])
    # {"Cheese": ["Quesadilla", "Sandwich"], "Salad": ["Salad", "Sandwich"], ...}
    ingr_list = []
    dish_list = []
    for key, value in sorted(ingr_dict.items()):
        if len(value) >= 2:
            ingr_list.append(key)
            dish_list.append(sorted(value))
    for i in range(len(dish_list)):
        dish_list[i].insert(0, ingr_list[i])
        
    return dish_list
    
```
