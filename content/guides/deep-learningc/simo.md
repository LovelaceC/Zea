---
title: The single input multiple output neural network
type: default
layout: page
child: Guides
---

## Theory

Let's take a look at the following neural network:

![Simple input multiple output](/guides/deep-learningc/img/simo1.png)

Following with the example in the previous entry, let's suppose we have the mood
of a person (sad - input) and we want to predict the temperature, the humidity
and air quality.

To predict the temperature, we take the input and we multiply it by the
temperature weight, to predict the humidity we multiply the input by the
humidity weight and finally, to predict the air quality, we multiply the
input by the air quality weight.

Simply put in pseudocode, this neural network would look like this:

```c
void
simple_input_multiple_output (input, vector, output)
{
  for (int i = 0; i < length_of_vector; i++)
    {
       output[i] = input * vector[i]
    }
}
```

* **input** represents the input to the neural network.
* **vector** represents an array containing the weights.
* **output** represents an array to store the predicted values.

This is how we would write this neural network in a much more simple way:

```c
temperature_prediction = sad * weight_temperature
humidity_prediction = sad * humidity_temperature
air_quality_prediction = sad * air_quality_temperature
```

## Implementation

The file `simple_input_multiple_output.c` looks like this:

```c
#include <stdio.h>
#define SAD 0.9
#define ARR_LEN 3

double predicted_results[3];

// temperature, humidity, air quality
double weights[3] = { -20, 95, 201 };

void
multiple_input_multiple_output (double input, double *weight, double *output, int len)
{
	for (int i = 0; i < len; i++)
	  {
		  output[i] = input * weight[i];
	  }
}

int
main (void)
{
	multiple_input_multiple_output (SAD, weights, predicted_results, ARR_LEN);
	printf ("Predicted temperature is: %f\n", predicted_results[0]);
	printf ("Predicted humidity is: %f\n", predicted_results[1]);
	printf ("Predicted air quality is: %f\n", predicted_results[2]);
	return 0;
}
```

What the function `multiple_input_multiple_output` is doing, is to multiply each
element of the array weight by the input and assign its result to each sub-i of
output.

After executing that code, we would get an output like the following:

```text
Predicted temperature is: -18
Predicted humidity is: 85.50
Predicted air quality is: 100.90
```

[Index](/guides/deep-learningc)
