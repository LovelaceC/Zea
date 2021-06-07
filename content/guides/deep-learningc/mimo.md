---
title: The multiple input multiple output neural network
type: default
layout: page
child: Guides
---

## Theory

Let's take a look at the multiple input multiple output neural network. The
multiple input multiple output is a combination of the multiple inputs single
outputs neural network.

Let's say that given the temperature, humidity and air quality apart from just
wanting to predict whether a person is happy or sad, we also want to predict
whether they are sick or healthy as well as predict whether they are active or
inactive. This is how this neural network looks like:

![MIMO Network](/guides/deep-learningc/img/mimo1.png)

The simplest way to solve this is to view it as three separate multiple input
single output neural networks. First, we take the input of temperature, humidity
and air quality, we multiply each input with its respective weight and add up
the three product, then we get the prediction for happy or sad, we repeat the
same to predict sick or healthy and then we repeat it again to get active or
inactive. Note that the inputs for predicting the three outputs are the same,
however, the weights are different:

```c
//              temp, hum, air
weights[][] = {{ 0.2, 0.1, 0.5 }, sad?
               { 0.3, 0.5, 0.6 }, sick?
			   { 0.0, 0.8, 0.7 }  active?
}
```

The different sets of weight is used to predict the three different output, we
can arrange the weights as a two dimensional array like this: the first row
represents the weight for the prediction for sad or happy, the second row
represents the weight for the prediction for sick or healthy and the third row
represents the weight for the prediction of active or inactive.

In this arrangement, the first column in each row represents the weight for the
temperature inputs, the second column represents the weight for the humidity
input and the third represents the weight for the air quality input. To compute
the multiple input multiple output neural network we have to perform a vector
matrix multiplication.

```c
void
vector_matrix_multiply (vector, matrix, output)
{
	for (int i = 0; i < length_of_vector; i++)
  	  {
		  output[i] = weighted_sum (vector, matrix[i]);
	  }
}
```

`vector` is the one dimentional array that contains our inputs and the matrix is
the two dimensional array that contains the weights. That pseudocode will
compute the predictions of our multiple inputs, multiple outputs

## Implementation

The file **multiple_input_multiple_output.c** looks like this:

```c
#include <stdio.h>
#define SAD 0.9
#define INPUT_LEN 3
#define OUTPUT_LEN 3

double predicted_results[3];
double weights[OUTPUT_LEN][INPUT_LEN] = {  { -2, 9.5, 2.01 },
	                                       { -0.8, 7.2, 6.3 },
										   { -0.5, 0.45, 0.9 }
									    };
double inputs[INPUT_LEN] = { 30, 87, 110 };

void
multiple_input_multiple_output (
	                              double *input_vector,
								  int input_len,
								  double *output_vector,
								  int output_len,
								  double weight_matrix[output_len][input_len]
	                           )
{
	for (int k = 0; k < output_len; k++)
     {
		 for (int i = 0; i < input_len; i++)
		   {
			   output_vector[k] += input_vector[i] * weight_matrix[k][i];
		   }
	 }
}

int
main (void)
{
	multiple_input_multiple_output (inputs, INPUT_LEN, predicted_results, OUTPUT_LEN, weights);
	printf ("Sad prediction: %f\n", predicted_results[0]);
	printf ("Sick prediction: %f\n", predicted_results[1]);
	printf ("Active prediction: %f\n", predicted_results[2]);
	return 0;
}
```

And you would get an output like the following:

```bash
Sad prediction: 987.600000
Sick prediction: 1295.400000
Active prediction: 123.150000
```
