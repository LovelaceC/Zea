---
title: Receiving Input
type: default
layout: page
child: Programming
---

In the program discussed previous, we assumed that the values of **principle**,
**number_of_years** and **rate** to be 1000, 3 and 8.5. Every time we run the
program we would get the same value for simple interest. If we want to calculate
simple interest for some other set of values then we are recquired to make the
relevant change in the program, and again compile and execute it. Thus, the
program is not general enough to calculate a simple interest for any set of
values without being required to make a change in the program. Moreover, if you
distribute the program to somebody, that person would not be able to make
changes in the program. Hence, it is a good practise to create a program that is
general enough to work for any set of values.

To make the program general, the program itself should ask the user to supply
the values of **principle**, **number of years** and **rate** through the
keyboard during execution. This can be achieved using a function called
**scanf()**. This function is a counter-part of the **printf()** function.
Printf outputs the values to the screen, whereas **scanf()** receives them from
the keyboard. This is illustrated in the program shown below:

```c
int
main ()
{
	int principle, number_of_years;
	float rate, simple_interest;
	printf ("Enter the values of principle, number of years and rate: ");
	scanf ("%d %d %f", &principle, &number_of_years, &rate);

	simple_interest = principle * number_of_years * rate / 100;
	printf ("%f\n", simple_interest);

	return 0;
}
```

The first **printf** outputs the message '_Enter the values of principle, number
of years and rate_" on the screen. Here, we have not used any expression in
**printf** which means that using expressions in **printf** is optional.

Note that the ampersand (**&**) before the variable names in the **scanf**
function is a must. **&** is an 'Address of' operator. It gives the location
number used by the variable in memory. When we say **&a**, we are telling
**scanf()** at which memory location it should store the value supplied by the
user from the keyboard. The detailed working of the **&** operator would be
taken up in future sections.

Note that a blank, a tab or a new line must separate the variables supplised to
**scanf**. Note that blank is created using spacebar, tab using the Tab key and
new line using the Enter key. This is shown below:

- The three values separated by blank:
  ```text
  1000 5 15.5
  ```
- The three values separated by tab:
  ```text
  1000    5    15.5
  ```
- The three values separated by newline:
  ```text
  1000
  5
  15.5
  ```

Here's another program using the **scanf** function:

```c
int
main ()
{
	int num;

	printf ("Enter a number: ");
	scanf ("%d", &num);

	printf ("Let me tell you a secret...\n");
	printf ("You have just entered the number %d\n", num);

	return 0;
}
```
