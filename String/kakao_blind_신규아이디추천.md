# 카카오 블라인드 '신규아이디 추천'
```python
import re

def func_1st(new_id):
    return new_id.lower()

def func_2nd(new_id):
    p = re.compile('[a-z0-9-_ | \.]')
    ret = ''
    for ch in new_id:
        if p.match(ch):
            ret += ch
    return ret
    # ...bat..y.abcdefghijklm
    
def func_3rd(new_id):
    p = re.compile('\.{2,}')
    sub = new_id
    while True:
        sub, cnt = p.subn('.', sub)
        if cnt == 0: break
    return sub

def func_4th(new_id):
    new_id = list(new_id)
    if new_id and new_id[0] == '.':
        new_id.pop(0)
    if new_id and new_id[-1] == '.':
        new_id.pop()
    return ''.join(new_id)

def func_5th(new_id):
    if not new_id:
        return 'a'
    return new_id
    
def func_6th(new_id):
    if len(new_id) >= 16:
        new_id = new_id[:15]
    if new_id[-1] == '.': new_id = new_id[:-1]
    return new_id

def func_7th(new_id):
    last = new_id[-1]
    while len(new_id) <= 2:
        new_id += last
    return new_id

def solution(new_id):
    new_id = func_1st(new_id)
    new_id = func_2nd(new_id)
    new_id = func_3rd(new_id)
    new_id = func_4th(new_id)
    new_id = func_5th(new_id)
    new_id = func_6th(new_id)
    new_id = func_7th(new_id)
        
    return new_id
```
