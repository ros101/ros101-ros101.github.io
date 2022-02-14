---
layout: notes
---
# Exercise 1
Write a script that imports the Phone and Laptop classes. These classes are found in the tech module. Your script must import the classes as follows:

```
import tech
```

Instantiate an instance of the Phone class and call it my_phone. It should have the name "Pixel 5", the color "sage", and 128 gigabytes of storage.

Instantiate an instance of the Laptop class and call it my_laptop. It should have the name "MacBook Pro", a size of 15 inches, and 256 gigabytes of storage.

## Expected Output
Print out both my_phone and my_laptop. You should see the following output.

|Print Statement|Output|
| print(my_phone)|A sage Pixel 5 with 128GB of storage.|
|print(my_laptop)|15-inch MacBook Pro with 256GB of storage.|

# Solution

```
import tech

my_phone = tech.Phone("Pixel 5", "sage", 128)
print(my_phone)

my_laptop = tech.Laptop("MacBook Pro", 15, 256)
print(my_laptop)
```
