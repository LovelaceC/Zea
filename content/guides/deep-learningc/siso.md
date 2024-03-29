---
title: The single input single output neural network
type: default
layout: page
child: Guides
---

## Theory

This is a very simple neural network that takes an input, a weight and generates
an output. The input interacts with the weight to produce the predicted value.

The following image represents this neural network:

![Simple Input Simple Output](/guides/deep-learningc/img/siso1.png)

Let's say that this is a simple neural network to predict whether a person is
sad or happy given a particular temperature.

In that simple example, we can consider sad or happy to be numerical values, we
could say that happy is a number above 10 and sad is a number below 10 (we will
see how to encode words into numerical values later).

The pseudocode of this neural network looks like this:

```c
int
simple_input_simple_output (input, weight)
{
  predicted_value = input * weight
  return predicted_value
}
```

In order to find a predicted value, we will just simply multiply the input value
by weight.

## Implementation

In order to implement this very simple neural network, we will need to create a
function, an array of inputs and (in my case) print the predicted values to the
screen.

The file **simple_input_simple_output.c** looks like this:

```c
#include <stdio.h>

double temperature[] = { 12, 23, 50, -10, 16 };
double weight = -2;

double
single_input_single_output (double input, double weight)
{
  return (input * weight);
}

int
main (void)
{
  printf ("%d\n", single_input_single_output (temperature[0], weight));
  printf ("%d\n", single_input_single_output (temperature[1], weight));
  printf ("%d\n", single_input_single_output (temperature[2], weight));
  printf ("%d\n", single_input_single_output (temperature[3], weight));
  printf ("%d\n", single_input_single_output (temperature[4], weight));

  return 0;
}
```

In that code, I am storing the inputs in the array `temperature` and the weight
in the variable `weight` whose value is `-2-. The predicted values are going to
be:

```text
-24
-46
-100
20
-32
```

If happy > 10 and sad < 9, based on the predicted value, the fourth value in the
array, corresponds to a person that is happy.

[Index](/guides/deep-learningc)
