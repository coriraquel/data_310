### Investigating the Dataset 
For this project we investigated the country_peron.csv dataset and classified the data using Keras Preprocessing Layers to specify, train and evaluate the model that predicts the wealth class versus all other classes as binary and categorical targets.
We will perform this process on the best and worst accuracies from our datasets. After preforming this process we will create a confusion matrix to further analyze our two producded results. 

### Evaluating Accuracies 
    For wealth class 2 (35476 points) -
    Loss: 0.5058
    Accuracy: 0.7019909024238586
    For wealth class 3 (38113 points) -
    Loss: 0.4481
    Accuracy: 0.7735379338264465
    For wealth class 4 (42191 points) -
    Loss: 0.2372
    Accuracy: 0.8971381187438965
    For wealth class 5 (43714 points) -
    Loss: 0.1082
    Accuracy: 0.9585234522819519
After evaluating our accuracies for each wealth class we can see that wealth class 2 was the least accurate and wealth class 5 was the most accurate. While an explination for this can be as simple as wealth class 5 having more available data points for training a more accurate model than wealth class 2 it is important to note that during this modeling process we added in a normalization function.  