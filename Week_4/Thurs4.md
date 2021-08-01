### Processing, vectorizing and predicting text
I began by downloading my dataset and taking a look at my text to better understand the data I was working with. 
I also printed the first 100 letters of my script to see the type of script I was using. 
I also checked to see how many individual characters were in my script. 

    65 unique characters
    Length of text: 1115394 characters
### Building and Training the Model 
Once I was down understanding my data I moved on processing the text through vectorization. I converted each character to an individual numeric ID.
After creating the IDs we made sure to convert back to alphabetical results after our processing to generate text. 
For the predicting task we created training examples and models. I divided the text into sample sequences with a specified length.Then for the target we produce the same length of the sample sequence +1. 
We created training batches by shuffling the data we put into sequences and putting it back into batches. 
We built the model with three layers: tf.keras.layers.Embedding, tf.keras.layers.GRU, and tf.keras.layers.Dense. This allows to model to look up the impeding, run the GRU timestep and apply the dense layer to generate predictions for the next layer. To get predictions you have to sample an output of the distribution but after this when it comes to Training the model it can be treated as a normal classification problem when it comes to adding in an optimizer, and a loss function.
### Generating Text 
We generate the text by running a loop and keeping track of the model's state as it's being used. I created a class called One Step to make a single step prediction. I increased my Epoch level to help the model form more complete sentences. I also adjusted the temperature parameter to create a more comprehensive script.