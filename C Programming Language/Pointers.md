# Pointers

## Overview

Pointer is a variable which stores a memory address.

## &var syntax

Ampersand is used to obtain the memory address of a value:

```
#include <stdio.h>

int main(void) {
  int age = 42;
  printf("The address of age is: %p", &age);
  return 0;
}
```

## Memory Addresses

Memory addresses are just numbers, they are usually written in hex.

## What are pointers?

Pointer is a variable which stores a memory address:

```
#include <stdio.h>

int main(void) {
  int age = 42;
  int *pointer = &age;

  printf("age: %d\n", age);
  printf("&age: %p\n", &age);
  printf("*pointer: %p\n", pointer);

  return 0;
}
```

You can't simply declare a variable which points to a memory address;
you have to use a pointer syntax:

```
#include <stdio.h>

int main(void) {
  int age = 42;
  int pointer = &age; // Compilation error at this point.
  return 0;
}
```

## Pass by value

In C, you pass structs by value: a copy of a struct is created when you pass it to a function.

## Dereferencing Pointers

Once you've got a pointer, you might obtain a value to which it points by using dereferencing:

```
int intVar = 42;
int *intVarPtr = &intVar;
int actualValue = *intVarPtr; // This now contains a value of 42.
```

## Different * meanings

So, * means three different things:

1. Pointer definition;
2. Dereferencing;
3. Changing a value of a pointer.

```
#include <stdio.h>

int main(void) {
  int intVar = 42;
  int *intVarPtr = &intVar;  // Define a pointer.
  *intVarPtr = 9;  // Change a value at a given memory address.
  printf("%d\n", intVar);
  printf("%p\n", intVarPtr);
  printf("%d\n", *intVarPtr);  // Dereference.
}
```

## -> syntax

`->` syntax is used to dereference a struct and access its field.
`(*structPtr).field` syntax is more explicit and less common.

## Arrays

Arrays are homogeneous and are stored contiguously in memory, just like structs.

## Array names as pointers

In C, an array name always points to the first element of an array.

## Pointer Size vs Array Size

Given a computer architecture, a pointer size is the same, whereas an array size is different.

## Array Decaying

Array decaying refers to a situation when an array name variable converts to a pointer
to the first element of the array.

Array decaying happens when you pass an array to a function, for example. This makes one
conclude that arrays are not passed by value.

## C Strings

C Strings are arrays of characters.

```
char *msg = "ssh terminal.shop for the best coffee";
```

The string above is stored contiguously in memory as an array of `char`s.
Note that when you declare a string you define a pointer to its first character.
The end and length of a string is determined by the null terminator: `\0`.

One interesting aspect of a string length is that most of the time it gets computed
on demand: there is no length associated with the string by default.

So, when you do:

```
printf("%s", stringVar);
```

We instruct the CPU to traverse the string until '\0' is encountered.

https://www.boot.dev/lessons/d3fe56ab-a7bf-4847-9fd7-299f1fe5fe03
