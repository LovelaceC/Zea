---
title: C Instructions
type: default
layout: page
child: Programming
---

Now that we have written a few programs let's look at the instructions that we
have used in these programs. There are basically three types of instructions in
C.

- Type Declaration Instruction
- Arithmetic Instruction
- Control Instruction

The purpose of each of these instructions is given below:

a) Type declaration instruction: To declare the type of variables used in a C
program.
b) Arithmetic instruction: To perform arithmetic operations between constants
and variables.
c) Control instruction: To control the sequence of execution of various
statements in a C program.

Since, the elementary C programs would usually contain only the type declaration
and the arithmetic instructions; we will discuss only these two instructions at
this stage. The other types of instructions will be discussed in detail in the
subsequent chapters.

## Type Declaration Instruction

This instruction is used to declare the type of variables being used in the
program. Any variable used in the program MUST be declared before using it in
any statement. For example:

```c
int bas;
float rs, grosssal;
char name, code;
```

There are several subtle variations of the type declaration instruction. These
are discussed below.

- While declaring the type of variable we can also initialise it as shown below:

  ```c
  int i = 10, j = 25;
  float a = 1.5, b = 1.99 + 2.4 * 1.44;
  ```

- The order in which we define the variables is sometimes important, sometimes
not. For example:

  ```c
  int i = 10, j = 25;
  ```

  Is the same as:

  ```c
  int j = 25, i = 10;
  ```

  However,

  ```c
  float a = 1.5, b = a + 3.1;
  ```

  is alright, but:

  ```c
  float b = a + 3.1, a = 1.5;
  ```

  is not. This is because here we are trying to use **a** even before defining
  it.

- The following statements would work:

  ```c
  int a, b, c, d;
  a = b = c = d = 10;
  ```

  However, the following statement would not work:

  ```c
  int a = b = c = d = 10;
  ```
  Once again we are trying to use **b** (to assign to **a**) before defining it.

## Arithmetic Instruction

A C arithmetic instruction consists of a variable name on the left hand side of
= and variable names and constants on the right side of the =. The variables and
constants appearing on the right hadn side pf = are connected by arithmetic
operators like **+**, **-**, **\*** and **/**.

For example:

```c
int ad;
float kpt, delta, alpha, beta, gamma;
ad = 3200;
kot = 0.0056;
delta = alpha * beta / gamma + 3.2 * 2 / 5;
```

Here:

- **\***, **/**, **-**, **=** are the arithmetic operators.
- **=** is the assignment operator.
- **2**, **5** and **3200** are integer constants.
- **3.2** and **0.0056** are real constants.
- **ad** is an integer variable.
- **kot**, **delta**, **alpha**, **gamma** are real variables.

The variables and constants together are called 'operands' that are operated
upon by the 'arithmetic operators' and the result is assigned, using the
assignment operator, to the variable on left-hand side.

A C arithmetic statement could be of three types. These are as follows:

- Integer mode arithmetic statement - This is an arithmetic statement in which
all operands are either integer variables or integer constants.

  ```c
  int i, king, us, me;
  i = i + 1;
  king = us * 234 + me - 7689;
  ```

- Real mode arithmetic statement - This is an arithmetic statement in which all
operands are either real constants or real variables.

  ```c
  float qbee, antink, si, prin, anoy, roi;
  qbee = antink + 23.123 / 4.5 * 0.3442;
  si = prin * anoy * ri / 100.0;
  ```

- Mixed mode arithmetic statement - This is an arithmetic statement in which
some of the operands are integers and some of the operands are real:

  ```c
  float si, prin, anoy, roi, avg;
  int a, b, c, num;
  si = prin * anoy * roi / 100.0;
  avg = (a + b + c + num) / 4;
  ```

It is very important to understand how the execution of an arithmetic
instruction takes place. Firstly, the right hand side is evaluated using
constants and the numerical values stored in the variable names. This value is
then assigned to the variable on the left hand side.

Though arithmetic instructions look simple to use, it is possible to commit
mistakes writing them. Let's take a closer look at these statements. Note the
following points carefully.

- C allows only one variable on left-hand side of **=**. That is, **z = k * l**
is legal, whereas **k * l = z** is illegal.

- In addition to the division operator, C also provides a modular division
operator. This operator returns the remainder on dividing one integer with
another. Thus, the expression 10 / 2 yields 5, whereas, 10 % 2 yields 0. Note
that on using % the sign of the remained is always the same of the numerator.
Thus, **-5 % 2** yields -1, whereas **5 % -2** yields 1.

- An arithmetic instruction is often used for storing character constants in
character variables.

  ```c
  char a, b, d;
  a = 'F';
  b = 'G';
  d = '+';
  ```

  When we do this, the ASCII values of the characters are stored in the
  variables. ASCII values are used to represent any character in memory. The
  ASCII values of 'F' and 'G' and 70 and 71 respectively

- The arithmetic operations can be performed on **ints**, **floats** and
**chars**. Thus, the statements:

  ```c
  char x, y;
  int z;
  x = 'a';
  y = 'b';
  z = x + y;
  ```

  are perfectly valid, since the addition is performed on the ASCII values of
  the characters and not on characters themselves. The ASCII values of 'a' and
  'b' are 97 and 98, hence, can definitely be added.

- No operator is assumed to be present. It must be written explicitely. In the
following example, the multiplication operator after b must be explicitely
written.

  ```c
  a = c.d.b(xy)             Usual arithmetic statement
  a = c * b * d * (x * y)   C statement
  ```

- Unlike other high level languages, there is no operator for performing
exponentiation operation. Thus, following statements are invalid:

  ```c
  a = 3 ** 2;
  b = 3 ^ 2;
  ```

  If we want to do the exponentiation, we can get it done this way:

  ```c
  #include <math.h>

  int
  main ()
  {
    int a;
	a = pow (3, 2);

	printf ("%d\n", a);

	return 0;
  }
  ```

  Here **pow** is a function of the standard library. It is being used to raise
  3 to the power of 2. **#include <math.h>** is a preprocessor directive. It is
  being used here to ensure that the **pow** function works correctly. We will
  learn more about standard library functions and preprocessor later.
