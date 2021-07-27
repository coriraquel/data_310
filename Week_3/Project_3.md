### Investigating the Dataset 
For this project we investigated the country_peron.csv dataset and classified the data using Keras Preprocessing Layers to specify, train and evaluate the model that predicts the wealth class versus all other classes as binary and categorical targets.
We will perform this process on the best and worst accuracies from our datasets. After preforming this process we will create a confusion matrix to further analyze our two producded results. 

### Evaluating Accuracies 
    For Wealth Class 1 (33382 points)- 
    LossL 0.4225
    Accuracy: 0.7533
    For wealth class 2 (35476 points) -
    Loss: 0.4197
    Accuracy: 0.7579
    For wealth class 3 (38113 points) -
    Loss: 0.4190
    Accuracy: 0.7587
    For wealth class 4 (42191 points) -
    Loss: 0.4202
    Accuracy: 0.7621
    For wealth class 5 (43714 points) -
    Loss: 0.4184
    Accuracy: 0.7563
For this original test I ran the accuracies with the only modification being that I dropped columns that were not in use. Nothing was coded as binary or categorical, the model ran like the example model in tensorflow. After evaluating our accuracies for each wealth class we can see that wealth class 1 was the least accurate and wealth class 4 was the most accurate. While an explanation for this can be as simple as wealth class 4 having more available data points for training a more accurate model than wealth class 1 it is important to note that during this modeling process we added in a normalization function.  

### Binary Modeling Process 
For the binary process I began by reading in the country_persons.csv file and cleaning my data. I decided to start out with a much smaller set of features to pull from in hopes of easing the process of getting rid of additional noise. After removing the usued columns I created a new target column in my dataframe then split the remaining data I had into testing and training data.

    dataframe = dataframe.drop(columns=['weights','unit','pnmbr','hhid','location','size'])
