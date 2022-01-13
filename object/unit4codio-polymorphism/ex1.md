---
layout: notes
---
# Exercise 1
Use the Lottery class to the left as the parent class. Create the PowerBall class as a child class of Lottery. Override the shuffle method so that it returns a list of six random integers between 1 and 99.

# Solution

```
import random

class Lottery:
  def shuffle(self):
    results = []
    for i in range(5):
      results.append(random.randint(1, 20))
    return results

class PowerBall(Lottery):
  def shuffle(self):
    results = []
    for i in range(6):
      results.append(random.randint(1, 99))
    return results
```
