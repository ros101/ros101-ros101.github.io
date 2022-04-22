---
layout: notes
---
# Faceted Data

Essentially, the proposal of Schmitz et al. (2016) is a framework to separate concerns depending on the context. Aspect-Oriented Programming (AOP) is a generic technique to separate concerns and weave them together into a coherent program (Elrad et al., 2001).

As defined in the popular AOP Java framework AspectJ (Kiczales et al., 1997), AOP consists in:
- Join points: execution points to be enhanced by a rule. Examples are methods (including getters and setters) and constructors, before or after the execution, or exception handling.
- Pointcuts: rule-based definition of join points. Examples are matching based on method signatures, return types or parameters.
- Aspects: a method-like logic that can be attached to a pointcut. They are implemented as static methods to be executed before, after, or "around" the pointcut.

AOP is a solution to program cross-cutting concerns such as logging, transactionality, and security. Its main advantage is to make these concerns transparent to the developer that can focus on the main business logic. Another advantage is that, with AOP, it becomes easy to centralize logic instead of duplicating it in several different components.

The main disadvantage of AOP is the lack of transparency for the developer. One of its advantages has a downside: the developer may not be aware of the injection of code that effectively modifies the flow and the outputs. That may be confusing and hard to debug.

The following is a simple implementation in Python. Join points are methods, decorators define pointcuts, and functions define the advice to be executed "around" the decorated method.

This implementation creates the decorator `@secure` switching the `Context` from `NORMAL` to `SAFE`. Methods decorated with `@secure` are not executed when the `Context` is `NORMAL`.

```python
class Faceted:

    from enum import Enum

    class Context(Enum):
        NORMAL = 'normal',
        SAFE = 'safe'

    @staticmethod
    def secure(func):
        def inner(*args, **kwargs):
            Faceted.secure_context = Faceted.Context.SAFE
            func(*args, **kwargs)
            Faceted.secure_context = Faceted.Context.NORMAL
        return inner

    @staticmethod
    def protect(func):
        def inner(*args, **kwargs):
            return func(*args, **kwargs) if Faceted.secure_context == Faceted.Context.SAFE else '***'
        return inner

class Data:

    def __init__(self, user:str, password:str) -> None:
        self._user = user
        self._password = password

    @property
    def user(self):
        return self._user

    @property
    @Faceted.protect
    def password(self):
        return self._password


data = Data('alberto', 'secret1!')

@Faceted.secure
def process_user(data:Data):
    print(f'username: [{data.user}] password: [{data.password}]')

def log_user(data:Data):
    print(f'username: [{data.user}] password: [{data.password}]')

process_user(data)
log_user(data)
process_user(data)
```

The output is

```
username: [alberto] password: [secret1!]
username: [alberto] password: [***]
username: [alberto] password: [secret1!]
```

## References

Elrad, T., Filman, R. E., & Bader, A. (2001). Aspect-oriented programming: Introduction. Communications of the ACM, 44(10), 29-32.

Kiczales, G., Lamping, J., Mendhekar, A., Maeda, C., Lopes, C., Loingtier, J. M., & Irwin, J. (1997, June). Aspect-oriented programming. In European conference on object-oriented programming (pp. 220-242). Springer, Berlin, Heidelberg.

Schmitz, T., Rhodes, D., Austin, T.H., Knowles, K., Flanagan, C. (2016) Faceted Dynamic Information Flow via Control and Data Monads. In: Piessens F., Viganò L. (eds) Principles of Security and Trust. POST 2016. Lecture Notes in Computer Science, vol 9635. Springer, Berlin, Heidelberg.
