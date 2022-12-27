### Implement linked list

#### 1. convert string to single charactered linked list
#### 2. replace input string in the linked list with white space

```python
import time


class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class LinkedList:
    def __init__(self):
        self.head = None

    def replace(self, string):
        head = self.head
        while head.data == string and head.next is not None:
            head = head.next
        self.head = head
        if self.head.data == string: self.head.data = None

        cur = head
        while cur.next is not None:
            nxt = cur.next
            if nxt.data == string:
                if nxt.next is None:
                    cur.next = None
                else:
                    cur.next = nxt.next
            else: cur = nxt

    def add(self, data):
        newNode = Node(data)
        return newNode

    def string_to_SLL(self, text):
        head = Node(text[0])
        self.head = head
        curr = head
        for i in range(1, len(text)):
            curr.next = self.add(text[i])
            curr = curr.next

        return head


    def print_(self, head):
        while head.next is not None:
            print(head.data + ' -> ', end='')
            head = head.next
        if head.data is not None:
            print(head.data)


text = 'a' * 10_000_000 + 'b'
llist = LinkedList()
ssl = llist.string_to_SLL(text)
# llist.print_(ssl)

s = time.time()
llist.replace('a')
e = time.time()
print(e-s)

llist.print_(llist.head)
```
