# C Basics

## Types

`int`, `float`, `char`.

Note: you have to use `'` quotes for a char type.

If you want to define a string, use: `char *msg_to_myself = "Keep going, man!";`
Note the usage of the double quotes above.
Strings in C is an array of characters.

## Variable Declarations

```
#include <stdio.h>


int main() {
  int age = 22;
  float numberOfNeuronsInMyBrain = 1.99;
  char sex = 'm';
  char *msgToMyself = "Keep it up, man!";
  // Note the distinction between quotes above.

  // Somewhere later...

  printf("Age = %d\n", age);
  printf("neu = %f\n", numberOfNeuronsInMyBrain);
  printf("sex = %c\n", sex);
  printf("msg = %s\n", msgToMyself);
}
```

## Format Specifiers

In the following line: `printf("Hello, %s. You're %d years old.\n", name, age);`,
the percent syntax is what's known as format specifiers.

## Functions

```
#include <stdio.h>

void printName(char *name) {
    printf("Hello, %s!\n", name);
}

void justAlarm(void) {
    // There are two use cases for void, as far as I know.
    // The first tells that a function returns no arguments,
    // The second tells that a function accepts no arguments.

    printf("Danger! Danger! Danger!");
}

float get_average(int x, int y, int z) {
  // Note the usage of 3.0 below.
  // If you were to just write 3, integer arithmetic would be performed.

  return (float)((x + y + z) / 3.0);
}


int main() {
    printName("Vlad");
    justAlarm();
    return 0;
}
```

In C, you are allowed to return only one value from a function.
To emulate the return of multiple values, use structs:

https://www.boot.dev/lessons/dba30100-5b2f-44a7-8469-e5bd1c0aad62

## .h and .c file extensions

`.h` files are called headers or interface files - these files
contain function declarations.

`.c` files are called C files or implementation files - these files
contain function implementations.

https://utat-ss.readthedocs.io/en/master/c-programming/c_h_files.html

## x++, x-- and ++x, --x

`x++` - post increment, or postfix notation.
`++x` - pre increment or prefix notation.

https://www.boot.dev/lessons/1e39fc85-e89f-454d-a324-d454bbced78d

## Short-Circuit Evaluation

C has a short-circuit evaluation.

```
if (x != 0 && 10 / x > 2) {
    // The division only happens if x != 0
    // This prevents a division by zero error
    printf("Safe!\n");
}
```

## Operator Precedence

`!` operator has a greater precedence than `&&`,
whereas `&&` has a greater precedence than `||`.

Use parentheses to avoid ambiguity.

## Ternary Operator

`int max = a > b ? a : b;`

## Type Sizes

Sizes of types vary depending on the underlying architecture.

## sizeof

One uses sizeof as a function or a unary operator to get
the size of a type or a variable in C.

## size_t

`size_t` is in unsigned integer which is returned by a `sizeof`.

https://en.cppreference.com/w/c/types/size_t.html
https://www.boot.dev/lessons/8f6f58b6-eb4c-420c-849f-27f8e7775f06

# TODO: What does size_t really mean? In which context is it used?

## Types of Loops in C

C has to following types of loops:

* for;
* while;
* do while.

In do while loops, put `;` after the while condition.

# TODO: In macros they for some reason omit `;`.

https://www.boot.dev/lessons/83509cbe-b879-46c5-a04a-4e5959b7e1f3

## Macros

https://gcc.gnu.org/onlinedocs/cpp/Macros.html

## Pragma Once

Use this if you want to include a file only once.

# TODO: Investigate how headers files work in C.

https://www.boot.dev/lessons/167c2f37-26bf-4305-ae7e-6d2e54d4afa5
