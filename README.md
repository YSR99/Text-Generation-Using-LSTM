
Text Generation Using LSTM

This project implements a text generation model using Long Short-Term Memory (LSTM) networks with TensorFlow and Keras. The model is trained on Shakespeare's text, allowing it to generate text in a similar style based on a given seed string.

Table of Contents


Usage
Model Architecture
Parameters
Examples




Usage:
To generate text, you need to run the text_generator.py script. This will load the trained model, and you can specify a seed string and the length of the text you want to generate.

Example
python
Copy code
import numpy as np
import random

# Assuming your model, char_to_index, and index_to_char are already defined

start_text = "In the quiet of the night, "
generated_text = generate_text(model, start_text, length=300, temperature=0.5)
print("Generated Text:\n", generated_text)
Function Details
generate_text(model, start_string, length=100, temperature=1.0):
model: The trained LSTM model.
start_string: The seed string from which to start generating text.
length: The number of characters to generate.
temperature: Controls the randomness of predictions (higher values = more randomness).
Model Architecture

The model consists of the following layers:

Input Layer: Takes sequences of characters as input.
LSTM Layer: A single LSTM layer with 128 units.
Dense Layer: A fully connected layer to produce output predictions for each character in the vocabulary.
Activation Layer: Uses softmax activation to output probabilities for each character.
Parameters

seq_length: The length of input sequences (40 characters).
STEP_SIZE: The step size for moving through the text (3 characters).
Batch Size: The model is trained with a batch size of 256.
Epochs: The model is trained for 4 epochs.
Examples

To generate text with different levels of creativity, you can change the temperature parameter:

python
Copy code
print('---------0.2---------')
print(generate_text(model, "To be or not to be, ", length=300, temperature=0.2))

print('---------0.4---------')
print(generate_text(model, "To be or not to be, ", length=300, temperature=0.4))

print('---------0.6---------')
print(generate_text(model, "To be or not to be, ", length=300, temperature=0.6))

print('---------0.8---------')
print(generate_text(model, "To be or not to be, ", length=300, temperature=0.8))

print('---------1.0---------')
print(generate_text(model, "To be or not to be, ", length=300, temperature=1.0))
