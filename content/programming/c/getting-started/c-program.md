---
title: The First C Program
type: default
layout: page
child: Programming
---

Armed with the knowledge about the types of variables, constants and keywords
the next logical step is to combine them to form instructions. However, istea
of this, we will write our first C program now. Once we have done that, we will
see in detail the instructions that it made use of.

Before we begin with our first C program, remember the following that are
applicable to all C programs:

- Each instruction in a C program is written as a separate statement. Therefore,
a complete C program would comprise of a series of statements.
- The statements in a program must appear in the same order in which we wish
them to be executed; unless, of course, the logic of the project demands a
liberate '_jump_' or transfer of control to a statement, which is out of
sequence.
- Blank spaces might be inserted between two words to improve the readability of
the statement. However, no blank spaces are allowed within a variable, constant
or keyword.
- All statements are entered in small-case letters.
- C has no specific rules for the position at which statements has to be
written. That's why it is often called a free-form language.
- Every C statement must end with a **;**. Thus, **;** acts as a statement
terminator.

Let's now write down our first C program. It will simply calculate simple
interest for a set of values representing principle, number of years and rate of
interest.

```c
/**
 * Calculation of simple interest
 */

int
main ()
{
	int principle, number_of_years;
	float rate, simple_interest;

	principle = 1000;
	number_of_years = 3;
	rate = 8.5;

	/* Formula for simple interest. */
	simple_interest = principle * number_of_years * rate / 100;

	printf ("%f\n", simple_interest);

	return 0;
}
```

Now a few useful tips about the program:

- Comments about the program should be enclosed within **/* */**. For example,
the first statement in our program is a comment.
- Though comments are not necessary, it is a good practise to begin a program
with a comment indicating the purpose of the program, its author and
\- occasionally - the date on which the program was written.
- Any number of comments can be written at any place in the program. For
example, a comment can be written before the statement, after the statement or
within the statement as shown below:

  ```c
  /* formula */ simple_interest = principle * number_of_years * rate / 100;
  simple_interest = principle * number_of_years * rate / 100; /* formula */
  simple_interest = principle * number_of_years * rate / /* formula */ 100;
  ```

- Sometimes it is also not so obvious what a particular statement in a program
accomplishes. At such times, it is worth mentioning the purpose of the statement
(or set of statements) using a comment. For example:

  ```c
  /* Formula for simple interest */
  simple_interest = principle * number_of_years * rate / 100;
  ```

- Often, programmers seem to ignore writing comments. But when a team is
building big software, well-commented code is almost essential for other team
members to understand it.
- Although a lot of comments are probably not necessary in this program, it is
usually the case that programmers tend to use too fre comments rather than too
many. An adequate number of comments can save hours of misery and suffering when
you later try to figure out what the program does.
- The normal language rules do not apply to text written wihin **/* */**. Thus,
we can type this text in small case, capital or a combination. This is because
the comments are solely for the understanding of the programmer or the fellow
programmers and are completely ignored by the compiler.
- Comments cannot be nested. For example:

  ```c
  /**
   * Calc of SI
   * /*
   *  * Author: Bassara
   *  * Date: 6/7/2021
   *  */
   */
  ```
  Is invalid
- A comment can be split over more than one line, for example:

  ```c
  /**
   * This
   * is
   * a
   * multiline
   * comment
   */
  ```
- **int main()** is a collective name given to a set of statemens. This name has
to be **main()**, it cannot be anything else. All statements that belong to
**main()** are enclosed within a pair of braces **{ }** as shown below.

  ```c
  int
  main ()
  {
	  statement1;
	  statement2;
	  statement3;
  }
  ```
- Technically speaking, **main()** is a function (also called subroutine). Every
function has a pair of parentheses **()** associated with it. We will discuss
functions and their working in great detail in the following sections.
- Any variable used in the program must be declared before using it. For
example:

  ```c
  int principle, number_of_years;
  float rate, simple_interest;
  ```
- Any C statement always ends with a **;**. For example:

  ```c
  float rate, simple_interest;
  rate = 8.5;
  ```
- In the statement:

  ```c
  simple_interest = principle * number_of_years * rate / 100;
  ```

  **\*** and **/** are the arithmetic operators. The arithmetic operators
  available in C are **+**, **-**, **\*** and **/**. C is very rich in
  operators. There are about 45 operators available in C. Surprisingly, there
  are no operators for exponentiation... A slip, which can be forgive
  considering the fact that C has been developed by an individual and not by a
  comitee.

- Once the value of **simple_interest** is calculated it needs to be displayed
on the screen. Unlike other languages, C does not contain any instruction to
display output on the screen. All output to the screen is achieved using
ready-made library functions. One such function is **printf()**. We have used it
to display on the screen the value contained in **simple_interest**.

  The general form of **printf()** function is:

  ```c
  printf ("<format string>", <list of variables>);
  ```

  _\<format string\>_ can contain:

  * **%f** for printing real values.
  * **%d** for printing integer values.
  * **%c** for printing character values.

  In addition to format specifiers like **%f**, **%d** and **%c** the format
  string might also contain any other characters. These characters are printed
  as they are when the **printf()** is executed.

  Following are some examples of the usage of the **printf()** function:

  ```c
  printf ("%f", simple_interest);
  printf ("%d %d %f %f", principle, number_of_years, rate, simple_interest);
  printf ("Simple interest = %f", simple_interest);
  printf ("Principle = %d\nRate = %f", principle, rate);
  ```

  The output of the last statement would look like this:

  ```
  Principle = 1000
  Rate = 8.5
  ```

  What is **\\n** doing in this statement? It is called newline and it takes the
  cursor to the next line, Therefore, you get the output split over two lines.
  '\\n' is one of the several Scape Sequences available in C. These are
  discussed in detail in later sections.

  **printf()** can not only print values of variables, it can also print the
  result of an expression. An expression is nothing but a valid combination of
  constants, variables and operators. Thus, 3, 3 + 2, c and a + b * c - d all
  are valid expressions. The results of these expressions can be printed as
  shown below:

  ```c
  printf ("%d %d %d %d", 3, 3 + 2, c, a + b * c - d);
  ```

  Note that **3** and **c** also represent valid expressions.

In the following lesson you will learn how to compile and run this program.
