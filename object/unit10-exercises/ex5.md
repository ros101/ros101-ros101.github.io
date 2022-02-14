---
layout: notes
---
# Exercise 5
You are going to write a program that simulates an online shopping cart. Create the composite class ShoppingCart in the shopping_cart.py file, and create the component class Item in the item.py file. The tables below indicate which attributes and methods your classes will need to create.

## The Shopping Cart Class

Important, the ShoppingCart class should initialize the attributes to either a 0 or an empty list. Your ShoppingCart class should have the following attributes:

|Attribute|	Explanation|
|items|	List of Item elements|
|total|	Total value of all of the items in the shopping cart|

It should also have the following methods:

|Method|	Explanation|
|__init__|	The constructor should not take have any arguments|
|add_item|	Add an item to the shopping cart and then calls the calculate_total method|
|calculate_total|	Assigns the total value of the shopping cart to the total attribute|
|get_total|	Returns the total value of the shopping cart|
|get_num_items|	Returns the number of items in the shopping cart|
|get_items|	Returns a list of all of the items in the cart|
|__str__|	Returns a human-readable string; see the Expected Output section for the format|

## The Item Class

Important, the subtotal attribute is not passed to the constructor. Initialize this attribute with a 0. Your Item class should have the following attributes:

|Attribute|	Explanation|
|name|	Name of the item|
|price|	How much the item costs|
|quantity|	How many items you have|
|subtotal|	Value of all of the items|

It should also have the following methods:

|Method|	Explanation|
|__init__|	The order of the parameters should be name, price, and then quantity|
|calculate_subtotal|	Assigns the total value of the items to the subtotal attribute|
|get_subtotal|	Returns the subtotal attribute|
|__repr__|	Returns a precise object definition; see the Expected Output section for the format|

## Expected Output
You can check your work by opening the exercise5.py file. Instantiate the three Item objects and a ShoppingCart object. Then add the items to the cart.

```
item1 = Item('milk', 1.5, 1)
item2 = Item('apple', 5, 0.75)
item3 = Item('bread', 2, 2.25)
cart = ShoppingCart()

cart.add_item(item1)
cart.add_item(item2)
cart.add_item(item3)
```

Next, add some print statements to make sure you code is working as intended.

```
print(cart.get_total())
print(cart.get_num_items())
print(cart)
print(cart.get_items())
```

You should see the following output:

```
9.75
3
The cart has 3 items for a total of $9.75
[Item(milk, 1.5, 1, 1.5), Item(apple, 5, 0.75, 3.75), Item(bread, 2, 2.25, 4.5)]
```

# Solution

iten.py

```
class Item():
  def __init__(self, name, price, quantity):
    self.name = name
    self.price = price
    self.quantity = quantity
    self.subtotal = 0

  def calculate_subtotal(self):
    self.subtotal = self.price * self.quantity

  def get_subtotal(self):
    return self.subtotal

  def __repr__(self):
    return f'Item({self.name}, {self.price}, {self.quantity}, {self.subtotal})'
```

shopping_cart.py

```
class ShoppingCart():
  def __init__(self):
    self.items = []
    self.total = 0

  def add_item(self, item):
    self.items.append(item)
    self.calculate_total()

  def calculate_total(self):
    self.total = 0
    for item in self.items:
      item.calculate_subtotal()
      self.total = self.total + item.get_subtotal()

  def get_total(self):
    return self.total

  def get_num_items(self):
    return len(self.items)

  def get_items(self):
    return self.items

  def __str__(self):
    return f'The cart has {self.get_num_items()} items for a total of ${self.get_total()}'
```

excercise5.py

```
from item import Item
from shopping_cart import ShoppingCart

item1 = Item('milk', 1.5, 1)
item2 = Item('apple', 5, 0.75)
item3 = Item('bread', 2, 2.25)
cart = ShoppingCart()

cart.add_item(item1)
cart.add_item(item2)
cart.add_item(item3)

print(cart.get_total()) #9.75
print(cart.get_num_items()) #3
print(cart) #The cart has 3 items for a total of $9.75
print(cart.get_items()) #[Item(milk, 1.5, 1, 1.5), Item(apple, 5, 0.75, 3.75), Item(bread, 2, 2.25, 4.5)]
```
