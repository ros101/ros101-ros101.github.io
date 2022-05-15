---
layout: notes
---
# Codio - Producer/consumer

Source code:

```python
# code source: https://techmonger.github.io/55/producer-consumer-python/

from threading import Thread
from queue import Queue

q = Queue()
final_results = []

def producer():
    for i in range(100):
        q.put(i)


def consumer():
    while True:
        number = q.get()
        result = (number, number**2)
        final_results.append(result)
        q.task_done()


for i in range(5):
    t = Thread(target=consumer)
    t.daemon = True
    t.start()

producer()

q.join()

print (final_results)
```
{: file='sums.py'}

The Queue is used to decouple the producer and the consumers so that the producer does not depend on a consumer.

`q.put(i)` and `q.get()` are used to queue and extract elements from the queue. `q.join` is used to block the execution until the queue is fully processed.
