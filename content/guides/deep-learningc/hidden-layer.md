---
title: The hidden layer
type: default
layout: page
child: Guides
---

## Theory

Let's examine the neural network with hidden layer.

![](/guides/deep-learningc/img/hidden.png)

With these values:

```c
input_to_hidden_weights[][] = {
	{0.2, 0.1, 0.5}, // hid[0]
	{0.3, 0.5, 0.6}, // hid[1]
	{0.0, 0.8, 0.7}  // hid[2]
//  temp, hum, aqi
};

hidden_to_output_weights = {
	{0.4, 0.2, 0.3}, // sad?
	{0.5, 0.2, 0.1}, // sick?
	{0.2, 0.4, 0.8}  // active?
//hid[0], [1], [2]
};
```

The neural network with one hidden layer, is the combination of the multiple
inputs single output and the single input multiple output neural network.

Essentially, we take the output of one layer and feed it as input of another
layer. Later on in this course, you will understand why our neural network
requires hidden layers.

Let's see how the prediction of sad can be derived.

We start from the inputs by taking the temperature input, multiplying it by its
correspondent weight, taking the humidity input, multiplying it also by its
corresponding weight and then taking the air quality input and also multiplying
it by its correspondent weight. We then add the three products together and this
will give us the hidden zero, we then repeat the same sequence to derive
hid[1] and hid[2]. After we have derived hid[0], hid[1] and hid[2] we multiply
hid[0], hid[1] and hid[2] by the corresponding weight and then we add up the
three products to get the prodiction of sad.

To compute all predictions, we will have to perform two consecutive factor
matrix multiplications, we will have two sets of weights, the first set will be
the weight for the inputs to the hidden layer computation and the second set
will be the weight for the hidden layer to the output layer computation.

To compute our neural network, we first multiply our vector of input by the
matrix of input to hidden weight. In pseudo code, it would look like the
following:

```c
void
hidden_layer_nn (input, weights, predicted_values)
{
	vector_matrix_multiply (input, weights[0], hidden_pred);
	vector_matrix_multiply (hidden_pred, weights[1], predicted_values);
}
```

This should result in a vector and, like I mentioned earlier, a vector is simply
a one dimensional array. This vector should contain hid[0], hid[1] and hid[2],
we take this vector and multiply it by the hidden to output weight matrix. This
vector matrix multiplications will also result in a vector, the vector will
contain the predictions for sade, sick and active.

## Implementation

```c
#include <stdio.h>

#define IN_LEN 3
#define OUT_LEN 3
#define HID_LEN 3

double predicted_results[3];

double input_to_hidden_weights[OUT_LEN][IN_LEN] = {
  { -2, 9.5, 2.01 },  // hid[0]
  { -0.8, 7.2, 6.3 }, // hid[1]
  { -0.5, 0.45, 0.9 } // hid[2]
};

double hidden_to_output_weights[OUT_LEN][HID_LEN] = {
  { -1.0, 1.15, 0.11 },   // sad?
  { -0.18, 0.15, -0.01 }, // sick?
  { 0.25, -0.25, -0.1 }   // active?
};

double inputs[IN_LEN] = { 30, 87, 110 };

double hidden_pred_vector[HID_LEN];

void
matrix_vector_multiply (double *input_vector, int input_len,
                        double *out_vector, int out_len,
                        double weights[out_len][input_len])
{
  for (int i = 0; i < out_len; i++)
    {
      for (int k = 0; k < input_len; k++)
        {
          out_vector[k] += input_vector[i] * weights[k][i];
        }
    }
}

void
hidden_layer_nn (double *input_vector, int INPUT_LEN, int HIDDEN_LEN,
                 double in_to_hid_weights[HIDDEN_LEN][INPUT_LEN],
                 int OUTPUT_LEN,
                 double hid_to_out_weights[OUTPUT_LEN][HIDDEN_LEN],
                 double *output_vector)
{
  matrix_vector_multiply (input_vector, INPUT_LEN, hidden_pred_vector,
                          OUTPUT_LEN, in_to_hid_weights);
  matrix_vector_multiply (hidden_pred_vector, HIDDEN_LEN, output_vector,
                          OUTPUT_LEN, hid_to_out_weights);
}

int
main ()
{
  hidden_layer_nn (inputs, IN_LEN, HID_LEN, input_to_hidden_weights, OUT_LEN,
                   hidden_to_output_weights, predicted_results);

  printf ("Sad prediction: %f\nSick prediction: %f\nActive prediction: %f\n",
          predicted_results[0], predicted_results[1], predicted_results[2]);

  return 0;
}
```

And we'd get the following output:

```text
Sad prediction: 515.656500
Sick prediction: 15.310500
Active prediction: -89.265000
```
