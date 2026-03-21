# Currying

## Overview

Currying is the process of transforming a function which takes multiple arguments
into a series of functions which accept only one.

## Currying Example

The function below is an example of currying:

```
def box_volume(length):
    def box_volume_with_len(width):
        def box_volume_with_len_width(height):
            return length * width * height
        return box_volume_with_len_width
    return box_volume_with_len

```

```
final_volume = box_volume(3)(4)(5)
print(final_volume)
# 60
```
