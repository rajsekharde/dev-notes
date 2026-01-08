
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



**. Python and Redis Queue .**:

Redis Queue (RQ): Python library for queueing jobs and processing them in the background with workers. Uses Redis for backend storage of jobs.

eg:

from rq import Queue
from redis import Redis

redis_conn = Redis() # Establish a connection to Redis

q = Queue(connection=redis_conn) # Create a queue

result = q.enqueue(count_words_at_url, 'http://nvie.com')

-> count_words_at_url- A user defined function that takes a URL, downloads the content of the page at that URL, and counts the number of words. The function is enqueued as a job, which will be processed by a worker in the background.


**. Producer-Consumer Architecture: .**

Producer -> Queue -> Consumers

eg- FastAPI server (Producer) -> Redis Queue -> Python Workers (Consumers)

