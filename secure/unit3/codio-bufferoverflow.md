---
layout: notes
---
# Codio - Buffer overflow

## Example in C

```C
#include <stdio.h>

int main(int argc, char **argv)
{
char buf[8]; // buffer for eight characters
printf("Enter name: ");
gets(buf); // read from stdio (sensitive function!)
printf("%s\n", buf); // print out data stored in buf
return 0; // 0 as return value
}
```
{: file='bufoverflow.c'}

When executed

```bash
$ ./bufoverflow
Enter name: 12345678
12345678
$ ./bufoverflow
Enter name: 1234567890
1234567890
*** stack smashing detected ***: <unknown> terminated
Aborted (core dumped)
```

The function `char *gets(char *str)` reads from `stdin` and stores the data in `*str`. It stops reading only with new line or `EOF`. A buffer overflow is the result of reading a string longer than memory referenced by `*str`. In this case `*str`'s length is 8 chars.

## Example in Python

```python
buffer=[None]*10

for i in range (0,11):

    buffer[i]=7

print(buffer)
```
{: file='bufoverflow.c'}

When executed

```
$ python3 Overflow.py
Traceback (most recent call last):
  File "Overflow.py", line 3, in <module>
    buffer[i]=7
IndexError: list assignment index out of range
```
{: file='Overflow.py'}

Installing pylint

```
$ pip3 install pylint
```

Running pylint

```
$ pylint Overflow.py
************* Module Overflow
Overflow.py:4:0: C0303: Trailing whitespace (trailing-whitespace)
Overflow.py:5:0: C0304: Final newline missing (missing-final-newline)
Overflow.py:1:0: C0103: Module name "Overflow" doesn't conform to snake_case naming style (invalid-name)
Overflow.py:1:0: C0114: Missing module docstring (missing-module-docstring)

-----------------------------------
Your code has been rated at 0.00/10
```

`pylint` was not useful to fix the error.
