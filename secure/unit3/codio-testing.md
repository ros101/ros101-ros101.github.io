---
layout: notes
---
# Codio - Testing

## equivalence

```python
# CODE SOURCE: https://stackoverflow.com/questions/38924421/is-there-a-standard-way-to-partition-an-interable-into-equivalence-classes-given/38924631#38924631

def equivalence_partition(iterable, relation):
    """Partitions a set of objects into equivalence classes

    Args:
        iterable: collection of objects to be partitioned
        relation: equivalence relation. I.e. relation(o1,o2) evaluates to True
            if and only if o1 and o2 are equivalent

    Returns: classes, partitions
        classes: A sequence of sets. Each one is an equivalence class
        partitions: A dictionary mapping objects to equivalence classes
    """
    classes = []
    partitions = {}
    for o in iterable:  # for each object
        # find the class it is in
        found = False
        for c in classes:
            if relation(next(iter(c)), o):  # is it equivalent to this class?
                c.add(o)
                partitions[o] = c
                found = True
                break
        if not found:  # it is in a new class
            classes.append(set([o]))
            partitions[o] = classes[-1]
    return classes, partitions


def equivalence_enumeration(iterable, relation):
    """Partitions a set of objects into equivalence classes

    Same as equivalence_partition() but also numbers the classes.

    Args:
        iterable: collection of objects to be partitioned
        relation: equivalence relation. I.e. relation(o1,o2) evaluates to True
            if and only if o1 and o2 are equivalent

    Returns: classes, partitions, ids
        classes: A sequence of sets. Each one is an equivalence class
        partitions: A dictionary mapping objects to equivalence classes
        ids: A dictionary mapping objects to the indices of their equivalence classes
    """
    classes, partitions = equivalence_partition(iterable, relation)
    ids = {}
    for i, c in enumerate(classes):
        for o in c:
            ids[o] = i
    return classes, partitions, ids


def check_equivalence_partition(classes, partitions, relation):
    """Checks that a partition is consistent under the relationship"""
    for o, c in partitions.items():
        for _c in classes:
            assert (o in _c) ^ (not _c is c)
    for c1 in classes:
        for o1 in c1:
            for c2 in classes:
                for o2 in c2:
                    assert (c1 is c2) ^ (not relation(o1, o2))


def test_equivalence_partition():
    relation = lambda x, y: (x - y) % 4 == 0
    classes, partitions = equivalence_partition(
        range(-3, 5),
        relation
    )
    check_equivalence_partition(classes, partitions, relation)
    for c in classes: print(c)
    for o, c in partitions.items(): print(o, ':', c)


if __name__ == '__main__':
    test_equivalence_partition()
```
{: file='equivalence.py'}

produces this output

```bash
$ python3 equivalence.py
{1, -3}
{2, -2}
{3, -1}
{0, 4}
-3 : {1, -3}
-2 : {2, -2}
-1 : {3, -1}
0 : {0, 4}
1 : {1, -3}
2 : {2, -2}
3 : {3, -1}
4 : {0, 4}
```

changing the conditions to `lambda x, y: x % 3 == y % 3` in `range(0, 10)` produces this output

```bash
$ python3 equivalence.py
{0, 9, 3, 6}
{1, 4, 7}
{8, 2, 5}
0 : {0, 9, 3, 6}
1 : {1, 4, 7}
2 : {8, 2, 5}
3 : {0, 9, 3, 6}
4 : {1, 4, 7}
5 : {8, 2, 5}
6 : {0, 9, 3, 6}
7 : {1, 4, 7}
8 : {8, 2, 5}
9 : {0, 9, 3, 6}
```

all numbers in the sets have the same result for `n % 3`

## styleLint

```python
# CODE SOURCE: SOFTWARE ARCHITECTURE WITH PYTHON

def factorial(n):
""" Return factorial of n """
if n == 0:
return 1
else:
return n*factorial(n-1)
```
{: file='styleLint.py'}

Running the code produces an error

```bash
$ python3 styleLint.py
File "styleLint.py", line 5
   """ Return factorial of n """
                               ^
IndentationError: expected an indented block
```

As an experiment I try `pylint`

```bash
$ pylint styleLint.py
************* Module styleLint
styleLint.py:5:29: E0001: invalid syntax (<unknown>, line 5) (syntax-error)
```

The result does not seem very useful. I fix the code:

```python
""" testing with python """

def factorial(number):
    """ Return factorial of number """
    if number == 0:
        return 1
    return number*factorial(number-1)

if __name__ == '__main__':
    print(factorial(5))

```
{: file='style_lint.py'}

I also renamed the file to `style_lint.py`. The code now outputs `120` and has a score of `10.00/10`

## pylintTest

```python
# SOURCE OF CODE: https://docs.pylint.org/en/1.6.0/tutorial.html

import string

shift = 3
choice = raw_input("would you like to encode or decode?")
word = (raw_input("Please enter text"))
letters = string.ascii_letters + string.punctuation + string.digits
encoded = ''
if choice == "encode":
  for letter in word:
    if letter == ' ':
      encoded = encoded + ' '
    else:
      x = letters.index(letter) + shift
      encoded=encoded + letters[x]
    if choice == "decode":
      for letter in word:
        if letter == ' ':
            encoded = encoded + ' '
        else:
          x = letters.index(letter) - shift
          encoded = encoded + letters[x]

print encoded
```
{: file='pylintTest.py'}

running `pylint` produces:

```bash
$ pylint pylintTest.py
************* Module pylintTest
pylintTest.py:26:13: E0001: Missing parentheses in call to 'print'. Did you mean print(encoded)? (<unknown>, line 26) (syntax-error)
```

I rename the file to `pylint_test.py` and proceed. The first run of `pylint` is `Your code has been rated at -8.42/10`

```python
""" testing in python """
import string

def encode():
    """ return encoded value """
    shift = 3
    choice = input("would you like to encode or decode?")
    word = (input("Please enter text"))
    letters = string.ascii_letters + string.punctuation + string.digits
    encoded = ''
    if choice == "encode":
        for letter in word:
            if letter == ' ':
                encoded = encoded + ' '
            else:
                index = letters.index(letter) + shift
                encoded=encoded + letters[index]
    if choice == "decode":
        for letter in word:
            if letter == ' ':
                encoded = encoded + ' '
            else:
                index = letters.index(letter) - shift
                encoded = encoded + letters[index]
    return encoded

print(encode())

```
{: file='pylint_test.py'}

After the corrections, the score is now `10.00/10`

running `flake8` on the original

```bash
$ flake8 pylint_test.py
pylint_test.py:4:1: E302 expected 2 blank lines, found 1
pylint_test.py:17:24: E225 missing whitespace around operator
pylint_test.py:27:1: E305 expected 2 blank lines after class or function definition, found 1
```

final version

```python
""" testing in python """
import string


def encode():
    """ return encoded value """
    shift = 3
    choice = input("would you like to encode or decode?")
    word = (input("Please enter text"))
    letters = string.ascii_letters + string.punctuation + string.digits
    encoded = ''
    if choice == "encode":
        for letter in word:
            if letter == ' ':
                encoded = encoded + ' '
            else:
                index = letters.index(letter) + shift
                encoded = encoded + letters[index]
    if choice == "decode":
        for letter in word:
            if letter == ' ':
                encoded = encoded + ' '
            else:
                index = letters.index(letter) - shift
                encoded = encoded + letters[index]
    return encoded


print(encode())

```
{: file='pylint_test.py'}

## metricTest

running flake8

```bash
$ flake8 metricTest.py
metricTest.py:13:8: E999 SyntaxError: invalid syntax
```

This is the original file

```python

#CODE SOURCE: SOFTWARE ARCHITECTURE WITH PYTHON

"""
2 Module metricTest.py
3
4 Metric example - Module which is used as a testbed for static
checkers.
5 This is a mix of different functions and classes doing
different things.
6
7 """
8 import random
9
10 def fn(x, y):
11 """ A function which performs a sum """
12 return x + y
13
14 def find_optimal_route_to_my_office_from_home(start_time,
15 expected_time,
16 favorite_route='SBS1K',
17 favorite_option='bus'):
18
19
20 d = (expected_time – start_time).total_seconds()/60.0
21
22 if d<=30:
23 return 'car'
24
25 # If d>30 but <45, first drive then take metro
26 if d>30 and d<45:
27 return ('car', 'metro')
28
29 # If d>45 there are a combination of optionsWriting Modifiable and Readable Code
[ 68 ]
30 if d>45:
31 if d<60:
32 # First volvo,then connecting bus
33 return ('bus:335E','bus:connector')
34 elif d>80:
35 # Might as well go by normal bus
36 return random.choice(('bus:330','bus:331',':'.
join((favorite_option,
37 favorite_route))))
38 elif d>90:
39 # Relax and choose favorite route
40 return ':'.join((favorite_option,
41 favorite_route))
42
43
44 class C(object):
45 """ A class which does almost nothing """
46
47 def __init__(self, x,y):
48 self.x = x
49 self.y = y
50
51 def f(self):
52 pass
53
54 def g(self, x, y):
55
56 if self.x>x:
57 return self.x+self.y
58 elif x>self.x:
59 return x+ self.y
60
61 class D(C):
62 """ D class """
63
64 def __init__(self, x):
65 self.x = x
66
67 def f(self, x,y):
68 if x>y:
69 return x-y
70 else:Chapter 2
[ 69 ]
71 return x+y
72
73 def g(self, y):
74
75 if self.x>y:
76 return self.x+y
77 else:
78 return y-self.x
```
{: file='metricTest.py'}

fixed version

```python
"""
Module metricTest.py

Metric example - Module which is used as a testbed for static
checkers.
This is a mix of different functions and classes doing
different things.

"""
import random


def fn(x, y):
    """ A function which performs a sum """
    return x + y


def find_optimal_route_to_my_office_from_home(start_time, expected_time,
                                              favorite_route='SBS1K',
                                              favorite_option='bus'):

    d = (expected_time - start_time).total_seconds()/60.0

    if d <= 30:
        return 'car'

    # If d>30 but <45, first drive then take metro
    if d > 30 and d < 45:
        return ('car', 'metro')

    # If d>45 there are a combination of optionsWriting
    # Modifiable and Readable Code
    if d > 45:
        if d < 60:
            # First volvo,then connecting bus
            return ('bus:335E', 'bus:connector')
        elif d > 80:
            # Might as well go by normal bus
            return random.choice(('bus:330', 'bus:331',
                                 ':'.join((favorite_option, favorite_route))))
        elif d > 90:
            # Relax and choose favorite route
            return ':'.join((favorite_option, favorite_route))


class C(object):
    """ A class which does almost nothing """

    def __init__(self, x, y):
        self.x = x
        self.y = y

    def f(self):
        pass

    def g(self, x, y):
        if self.x > x:
            return self.x + self.y
        elif x > self.x:
            return x + self.y


class D(C):
    """ D class """

    def __init__(self, x):
        self.x = x

    def f(self, x, y):
        if x > y:
            return x - y
        else:
            return x + y

    def g(self, y):
        if self.x > y:
            return self.x + y
        else:
            return y - self.x

```
{: file='metricTest.py'}

## sums

```python
def test_sum():
    assert sum([1, 2, 3]) == 6, "Should be 6"

if __name__ == "__main__":
    test_sum()
    print("Everything passed")
```
{: file='sums.py'}

running mccabe

```bash
$ python3 -m mccabe sums.py
4:0: 'test_sum' 1
If 7 2
```

and

```python
def test_sum():
    assert sum([1, 2, 3]) == 6, "Should be 6"

def test_sum_tuple():
    assert sum((1, 2, 2)) == 6, "Should be 6"

if __name__ == "__main__":
    test_sum()
    test_sum_tuple()
    print("Everything passed")
```
{: file='sums.py'}

```bash
$ python3 -m mccabe sums2.py
4:0: 'test_sum' 1
7:0: 'test_sum_tuple' 1
If 10 2
```

The code is clearly simple and there are no branches.
