
**Redis as a message queue:**

Queue- First In, First Out (FIFO)

Primary data structure used- Redis List

Redis List- List of strings sorted by the order of insertion. Elements can be to a Redis List on the head(left) or on the tail(right)

Commands to create a queue in Redis-

LPUSH- add an element to the head of the list.

LPUSH myqueue "Task1" : Creates a new list named "myqueue" and adds the string "Task1" to it. If the queue already exists, "Task1" is added to the head of the list.

Basic Queue operations:

Enqueue- LPUSH. eg- LPUSH myqueue "Task2"

Dequeue- RPOP. Removes and returns the element at the tail of the list. eg- RPOP myqueue - removes "Task1" and returns it

Peek- LRANGE. Returns the element at the tail of the list, which is the next to be dequeued. eg- LRANGE myqueue -1 -1

