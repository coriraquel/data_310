# Informal Reponse 

- Produce 3 new images: 
    - ![](images/Capture.png)
    - ![](images/Capture1.png)
    - ![](images/Capture3.png)
    
- Array of predictions other than example array: 
    - What does this array represent? 
      - Answer: how likely it is that the image corresponds to each of the ten labels presented 
    - How were the Softmax() and argmax() functions aplied? 
      - Answer: Softmax() was used to transform all the values in our predictions to a number between 0 and 1 in an attempt to make it easier for us to interpret. Argmax() gave us the highest value of these number aka which label/article of clothing the photo was most likely to be. 
    - Does the output label from np.argmax() match test_labels dataset?
      - Answer: yes for predicting image #1 both of my labels came out as 2
- Two Plotted Additional Images with image and predicted label: 
  - ![](images/Capture4.png)
  - ![](images/Capture5.png)
- New test dataset 
    - Does the predicted value match the test label?
      - Answer: Yes, it was predicted to be a pullover and it was 
    - Why did we not use Softmax() a second time? 
      - Answer: We did not use Softmax() because we were only grabbing the predictions for the single image in our batch instead of getting a list of lists for each image in the batch of data