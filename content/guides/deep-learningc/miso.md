---
title: The multiple input single output neural network
type: default
layout: page
child: Guides
---

## Theory

Let's increase the number of inputs.

Let's say we want to predict whether a person is sad or happy given the
temperature, the humidity and the air quality. This is how the neural network
would look like:

![Multiple input single output neural network](/guides/deep-learningc/img/miso1.png)

Note that we wave three weights (`w1`, `w2` and `w3`) one of them is for the
temperature, one for the humidity and the other one for the air quality. To
compute the predicted result, we perform something that is called the weighted
sum, this means we treat this neural network as three separate single input
single output neural networks and then we add the predicted values of the three
separate networks, this is what the pseudocode would look like:

```c
int
weighted_sum (inputs, weights, length_of_inputs)
{
  int output
  for (int i = 0; i < length_of_inputs; i++)
    {
		output += inputs[i] * weights[i]
    }
  return output
}
```

We multiply each single input by their respective weight and we add the
multiplication of their values to a variable called output, that is returned
once the computation is done.

Let's say we have three arrays, one to hold the temperature values, one to hold
the humidity values and another one to hold the air quality values:

```c
temperature[] = { 12, 23, 25, 27, 10, -5, 2, 13 };
humidity[] = { 60, 67, 75, 87, 50, 65, 66, 63 };
air_quality[] = { 60, 47, 175, 187, 50, 95, 76, 73 };
```

Now let's implement and test this neural network.

## Implementation

```c
#include <stdio.h>

#define INPUTS 3

double temperature[] = { 12, 23, 25, 27, 10, -5, 2, 13 };
double humidity[] = { 60, 67, 75, 87, 50, 65, 66, 63 };
double air_quality[] = { 60, 47, 175, 187, 50, 95, 76, 73 };

double weight[] = { -2, 2, 1 };

double
multiple_input_single_output (double *inputs, double *weights, int len)
{
  double output;

  for (int i = 0; i < len; i++)
    {
		output += inputs[i] * weights[i];
    }

  return output;
}

int
main (void)
{
  double training1[] = { temperature[0], humidity[0], air_quality[0] };

  printf ("The prediction of first three values is: %f\n",
multiple_input_single_output (training1, weight, INPUTS));

  return 0;
}
```

It might seem a little confusing at first, but let's get step by step through
it.

We are defining a constant `INPUTS` that defines how many inputs the neural
network contains, in this case three. We also have three arrays `temperature`,
`humidity` and `air_quality`, in our `main` function we are creating an array
`training1` that contains all the data to our neural predict a value, it
contains the first entry of each one of the three arrays, and finally, we are
printing the predicted value.

We'd get an output like the following:

```bash
The prediction of first three values is: 156.000000
```

[Index](/guides/deep-learningc)
