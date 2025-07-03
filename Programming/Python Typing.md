# Python Typing

Generics allow you to annotate containers with arbitrary types they might work with.

```
class LoggerVar[T]:
    ...
```
```
```

You can then parameterize generics at runtime:

```
from collections.abc import Iterable

def zero_all_vars(vars: Iterable[LoggedVar[int]]) -> None:
    for var in vars:
        var.set(0)
```
```
```

A captain informs: `Union[X, None] == X | None == Optional[X]`.
