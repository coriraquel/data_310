- Group Reponse Link:
  https://gwen013.github.io/data310/writeup01.html

Thursday Exercise with Liz Goodman, Cori Ingram, and Lydia Danas

The model is performing well and the training and validation accuracy and loss follow a very similar pattern.
The model accurately predicts what type of code the question input is pertraining to about 74% of the time so we can be realtively confident in our model. 3. export_model.predict(examples) array([[0.5513627 , 0.40722254, 0.4448905 , 0.5768401 ], [0.5875802 , 0.38242897, 0.5630223 , 0.45748726], [0.7534702 , 0.61576515, 0.38523862, 0.25435194]], dtype=float32
Label 0 corresponds to csharp Label 1 corresponds to java Label 2 corresponds to javascript Label 3 corresponds to Python
Python test: The model accurately categorized the question as a python tag.

Javascript test: The model did not accurately categorize the question as javascript and instead recognized it as csharp.

C# test: The model accurately categorized the question as a c# tag.
The most significant difference between the two models is the number of classifiers to determine if we use binary in the code. The multi-class model performed better and had higher accuracy and the training and testing data had a stronger correlation. The accuracy for the multiclass data was 0.7393749952316284 and the accuracy for the binary data was 0.8722400069236755.
Thursday Exercise

The model is performing well and the training and validation accuracy and loss follow a very similar pattern.
With an accuracy of about 74% we can use the test data to validate our model. 3. export_model.predict(examples) array([[0.5513627 , 0.40722254, 0.4448905 , 0.5768401 ], [0.5875802 , 0.38242897, 0.5630223 , 0.45748726], [0.7534702 , 0.61576515, 0.38523862, 0.25435194]], dtype=float32 Label 0 corresponds to csharp Label 1 corresponds to java Label 2 corresponds to javascript Label 3 corresponds to Python
Python test: The model accurately categorized the question as a python tag.

Javascript test: The model did not accurately categorize the question as javascript and instead recognized it as csharp.

C# test: The model accurately categorized the question as a c# tag.
The most significant difference ebtween the two models is how many classifications there are for the model to sort between as the mutli-class model had 4, but the binary class model had only two. The models for the multi-class data appeared to be more accurate as the training and test data followed more similar patterns than the binary data, however the binary test data produced an accuracy of about 87% whereas the multi-class test data produced an accuracy of about 74%. Based on the accuracies it seems that the binary data performed better and trained the model more effectively to produce better test results.