### Wednesday No Class Response 
Modify the existing filter and if needed the associated weight in order to apply your new filters to the image 3 times. Plot each result, upload them to your response, and describe how each filter transformed the existing image as it convolved through the original array and reduced the object size.
![one](C:\Users\corii\WebstormProjects\data_310\images\plot1.PNG)
![two](C:\Users\corii\WebstormProjects\data_310\images\plot2.PNG)
![three](C:\Users\corii\WebstormProjects\data_310\Week_2\plot3.PNG)
Each different filter learns how to isolate and take out specific features within them that are deemed important, this in turn changes the data set so that different details in the photo are emphasized. 

What are you functionally accomplishing as you apply the filter to your original array? 
I am implementing 3 arrays and 3 items as a filter to a image that I turned into an array to filter out specific features so that my computer can identify these features to better train my model. 

Why is the application of a convoling filter to an image useful for computer vision? 
This is usual because it helps save memory and time when a machine is attempting to fit a model because instead of trying to account for a large number of variable it is isolating similar features and running a model based off of the features that are seen consistently. 

Another useful method is pooling. Apply a 2x2 filter to one of your convolved images, and plot the result.
![plot4](C:\Users\corii\WebstormProjects\data_310\images\plot4.PNG)

In effect what have you accomplished by applying this filter? Does there seem to be a logic (i.e. maximizing, averaging or minimizing values?) associated with the pooling filter provided in the example exercise (convolutions & pooling)? Did the resulting image increase in size or decrease? Why would this method be useful?
I have found the least amount of the biggest pixels in the image after a series of iteration. Yes, there is logic because we are getting the smallest amount of the biggest value for this pooling feature. No in fact it was 1/4th in size of the old image. This can be useful when we don't want to lose any important information but want to filter out what's not needed for time and memory purposes. 

New Pixel Value= 0 
