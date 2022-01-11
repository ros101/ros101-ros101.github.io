---
layout: notes
---
# Exercise 4

Create the Median that has the method calculate_median that calculates the median of the integers passed to the method. Use method overloading so that this method can accept anywhere from two to five parameters.

## How to calculate median
The median can be thought of as the "middle" number in an ordered list of numbers. There are two numbers in the "middle", the median is the average of these two numbers.

|Method Call	Return Value|
|-|-|
|m.calculate_median(3, 5, 1, 4, 2)|3|
|m.calculate_median(8, 6, 4, 2)|5.0|
|m.calculate_median(9, 3, 7)|7|
|m.calculate_median(5, 2)|3.5|

# Solution

```
class Median:
  def calculate_median(self, a, b, c=None, d=None, e=None):
    v=[a,b]
    if c is not None:
      v.append(c)
      if d is not None:
        v.append(d)
        if e is not None:
          v.append(e)
    v.sort()
    if len(v)%2==1:
      return v[len(v)//2]
    else:
      return (v[len(v)//2]+v[len(v)//2-1])/2


m = Median()
print(m.calculate_median(3, 5, 1, 4, 2))
print(m.calculate_median(8, 6, 4, 2))
print(m.calculate_median(9, 3, 7))
print(m.calculate_median(5, 2))
```
