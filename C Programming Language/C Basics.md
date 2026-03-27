# C Basics

## The simplest program

```
int main() {
  return 0;
}
```

The entry point to any C program is a main function;
the return code of main determines whether the program finished successfully or not.

## Hello, World! example

```
#include <stdio.h>


int main() {
  printf("Hello, World!\n");
  return 0;
}
```

By the way, `printf` stands for print formatted.

## Comments

Two types of comments are available:

`// This a comment line.`
```
/*
  This
  is
  a
  comment
  block!
*/
```

## Types

`int`, `float`, `char`.

Note: you have to use `'` quotes for a char type.
If you want to define a string, use:

`char *msg_to_myself = "Keep going, man!";`

Note the usage of double quotes above.

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

## Compilation: types vs values

One can't change a variable type:
```

int main() {
    char *max_threads = "5";

    // call badcop
    // this is illegal
    max_threads = 5;
}
```

However, a variable value can be modified if `const` is not present:

```
int main() {
    int x = 5;
    x = 10; // this is ok
    x = 15; // still ok
}
```

Compare the code above to the following snippet:

```
int main() {
    const int x = 5;
    x = 10; // compilation error: value change of a const is prohibited.
}
```
