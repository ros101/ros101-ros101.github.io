---
layout: notes
---
# Exercise 5
Define the Cyclist class which has attributes name, nationality, and nickname. Use the Python convention to make these attributes private. Create the getters and setters using the property decorator.

## Expected Output
Initialize an object of the Cyclist class as follows:

```
my_cyclist = Cyclist("Greg LeMond", "American", "Le Montstre")
```

|Task	Output
|print(my_cyclist.name)|Greg LeMond|
|print(my_cyclist.nationality)|American|
|print(my_cyclist.nickname)|Le Monstre|
|my_cyclist.name = "Eddy Merckx"|N/A|
|my_cyclist.nationality = "Belgian"|N/A|
|my_cyclist.nickname = "The Cannibal"|N/A|
|print(my_cyclist.name)|Eddy Merckx|
|print(my_cyclist.nationality)|Belgian|
|print(my_cyclist.nickname)|The Cannibal|

## Important
Use the property decorator; follow the Python convention for private attributes.

# Solution

```
class Cyclist:
  def __init__(self, name, nationality, nickname):
    self._name=name
    self._nationality=nationality
    self._nickname=nickname

  @property
  def name(self):
    return self._name

  @name.setter
  def name(self, name):
    self._name=name

  @property
  def nationality(self):
    return self._nationality

  @nationality.setter
  def nationality(self, nationality):
    self._nationality=nationality

  @property
  def nickname(self):
    return self._nickname

  @nickname.setter
  def nickname(self, nickname):
    self._nickname=nickname

my_cyclist = Cyclist("Greg LeMond", "American", "Le Montstre")

print(my_cyclist.name)
print(my_cyclist.nationality)
print(my_cyclist.nickname)
my_cyclist.name = "Eddy Merckx"
my_cyclist.nationality = "Belgian"
my_cyclist.nickname = "The Cannibal"
print(my_cyclist.name)
print(my_cyclist.nationality)
print(my_cyclist.nickname)
```
