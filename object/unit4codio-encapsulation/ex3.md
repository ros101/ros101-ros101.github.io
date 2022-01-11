---
layout: notes
---
# Exercise 3

Define the BankAccount class which has attributes for checking and savings. Use the Python convention to make these attributes private. Create the getters get_checking and get_savings, and create the setters set_checking and set_savings.

## Expected Output
Initialize an object of the BankAccount class as follows:

```
my_account = BankAccount()
```

|Task|Output|
|-|-|
|my_account.set_checking(523.48)|N/A|
|print(my_account.get_checking())|523.48|
|my_account.set_savings(386.15)|N/A|
|print(my_account.get_savings())|386.15|

## Important
Do use the property decorator or function; follow the Python convention for private attributes.

# Solution

```
class BankAccount:
  def __init__(self):
    self._checking=0
    self._savings=0

  def get_checking(self):
    return self._checking

  def set_checking(self, checking):
    self._checking=checking

  def get_savings(self):
    return self._savings

  def set_savings(self, savings):
    self._savings=savings

my_account = BankAccount()

my_account.set_checking(523.48)
print(my_account.get_checking())
my_account.set_savings(386.15)
print(my_account.get_savings())
```
