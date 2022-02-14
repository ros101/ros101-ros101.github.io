---
layout: notes
---
# Exercise 3

Create the Dog class with attributes for name and breed. Then create a list of five dogs according to the following table:

|Dog|	Name|	Breed|
|1|	Marceline|	German Shepherd|
|2|	Cajun|	Belgian Malinois|
|3|	Daisy|	Border Collie|
|4|	Rocky|	Golden Retriever|
|5|	Bella|	Irish Setter|

Verify that the name and breed of the dogs in the list match the order of the table.

# Solution

```
class Dog():
  def __init__(self, name, breed):
    self.name = name
    self.breed = breed

dogs = [
  Dog('Marceline','German Shepherd'),
  Dog('Cajun','Belgian Malinois'),
  Dog('Daisy','Border Collie'),
  Dog('Rocky','Golden Retriever'),
  Dog('Bella','Irish Setter')
]
```
