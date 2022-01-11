---
layout: notes
---
# Exercise 2

Define the Artist class which has attributes for name, medium, style, and famous_artwork. Do not use the Python convention to make these attributes.

## Expected Output
Initialize an object of the Artist class as follows:

```
my_artist = Artist('Bill Watterson', 'ink and paper', 'cartoons', 'Calvin and Hobbes')
```

|Task|Output|
|Print the name attribute|Error Message|
|Print the medium attribute|Error Message|
|Print the style attribute|Error Message|
|Print the famous artwork attribute|Error Message|
|Print _Artist__name|Bill Watterson|
|Print _Artist__medium|ink and paper|
|Print _Artist__style|cartoons|
|Print _Artist__famous_artwork|Calvin and Hobbes|

## Important
You do not need to create any getters or setters; do not follow the Python convention for private attributes.

# Solution

```
class Artist:
  def __init__(self, name, medium, style, famous_artwork):
    self.__name=name
    self.__medium=medium
    self.__style=style
    self.__famous_artwork=famous_artwork

my_artist = Artist('Bill Watterson', 'ink and paper', 'cartoons', 'Calvin and Hobbes')


print(my_artist._Artist__name)
print(my_artist._Artist__name)
print(my_artist._Artist__style)
print(my_artist._Artist__famous_artwork)
```
