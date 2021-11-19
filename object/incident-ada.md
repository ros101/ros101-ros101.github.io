---
layout: notes
---
# Ariane 5 rocket explosion: Possible Measures
### Comment on peer's submission

## Possible measures

The vulnerable code was written in ADA (Lions, 1997). ADA is designed to detect potential errors at compile-time and potential overflows are part of the checks (Brosgol, 2006). In other words, the programming language used for the project should have protected the project from such failure.

It is possible, however, that different compilers may skip some controls or leave the decision to perform them to the developer (Stackexchange, 2016). It is also possible to write poor code that does trigger the compiler's checks.

It seems logical to conclude that a better training of the developers, or a stricter configuration in the developers' tools would prevent this kind of incidents.

Demonstration of the checks

I tested this possibility with a simple software, overflow.adb:

```
with Ada.Text_IO;
procedure Overflow with SPARK_Mode is
   X : Long_Float range 0.0 .. 3000000000.0 := Long_Float(integer'last);
   V : integer range 0 .. 1000;
begin
  V := Integer(X);
  Ada.Text_IO.Put_Line (integer'Image (V));
  X := X + 0.5;
  V := Integer(X);
  Ada.Text_IO.Put_Line (integer'Image (V));
end Overflow;
```

Variable X is defined as a 64bits Float ranging from 0 to 3.000.000.000 while variable V is defined between 0 and 1.000. This software should fail when X, incremented by 0.5 is converted into an integer.

Compilation:

```
gnatmake -f overflow.adb  -largs -Wl,-v
```

The software compiles without errors but it does not run failing immediately:

```
raised CONSTRAINT_ERROR : overflow.adb:7 range check failed
```

Defining a project, my_project.gpr:

```
project My_Project is
   for Source_Dirs use (".");
end My_Project;
```

and then running gnatprove:

```
gnatprove -P my_project.gpr
```

returns an error:

```
overflow.adb:7:08: medium: range check might fail (e.g. when X = 2.1474836470E+9)
```

It was possible to detect the potential overflow during the development.

## Demonstration of the failure

It is necessary to remove the range definition:

```
with Ada.Text_IO;
procedure Overflow with SPARK_Mode is
   X : Long_Float := Long_Float(integer'last);
   V : integer;
begin
  V := Integer(X);
  Ada.Text_IO.Put_Line (integer'Image (V));
  X := X + 0.5;
  V := Integer(X);
  Ada.Text_IO.Put_Line (integer'Image (V));
end Overflow;
```

The code compiles, but this time the code runs failing at runtime after the first print. This is the output:

```
2147483647
raised CONSTRAINT_ERROR : overflow.adb:10 overflow check failed
```

## Final note

Installing the ADA compiler is not simple, but it is possible to run the experiments in [onecompiler](https://onecompiler.com/ada)

Source is available: [overflow in ada on github](https://github.com/ros101/overflow-in-ada)


## References

Brosgol, B. M. (2006) Ada 2005: a language for high-integrity applications. CrossTalk–The Journal of Defense Systems, 19(8), 8-11.

Lions, J. L. (1997). Flight 501 Failure. Report by the Inquiry Board. Paris.

Stackexchange (2016) 'Why is overflow silently allowed in Ada?'. Available from https://softwareengineering.stackexchange.com/questions/324771/why-is-overflow-silently-allowed-in-ada [Accessed on 19/11/2021]
