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

    Model: "my_model"
    _________________________________________________________________
    Layer (type)                 Output Shape              Param #
    =================================================================
    embedding (Embedding)        multiple                  16896
    _________________________________________________________________
    gru (GRU)                    multiple                  3938304
    _________________________________________________________________
    dense (Dense)                multiple                  67650
    =================================================================
    Total params: 4,022,850
    Trainable params: 4,022,850
    Non-trainable params: 0
    _________________________________________________________________

    Epoch 50/50
    172/172 [==============================] - 10s 54ms/step - loss: 0.4188

### Generating Text 
We generate the text by running a loop and keeping track of the model's state as it's being used. I created a class called One Step to make a single step prediction. I increased my Epoch level to help the model form more complete sentences. I also adjusted the temperature parameter to create a more comprehensive script. I ran my model with 50 epochs to attempt to produce the most comprehensible script possible without having my model take a very long time to run. This is the script I ended up with. 

    ROMEO:
    The exile is more to love, and throw it you do:
    Come to the King of Naples thread:
    There is not so, that lives with slandered:
    Even so, sweet masters swo, to let him live.
    
    ROMEO:
    
    JUSt Conspirator:
    The wondrous man I can a respect
    There's not harder than by seconding.
    
    TRANIO:
    Call that, it is well alliance to make his
    as defended.
    
    VIRGILIA:
    There's this oath fair and me;
    And therefore, sent but wrongth us both to bear,
    My grief is spent; our graves lived to love,
    You'ld ammecter yourselves. Opposs
    His pleasure attending out.
    
    Citizens:
    Our own faithful yet and living
    makers may believe your treasure: hence!
    Depasted thy Deckboia a grain and virtuous,
    By death was proof another weak,
    And then deny her ready to my rich nor Conile beholding.
    
    TRANIO:
    Softly, with a pursuivant at a bawd! sir?
    
    MENENIUS:
    The lard give us our opitor. Aumerle
    This last to come, hearing you word.
    
    PAULINA:
    There's the nobles of the heart.
    
    BALTHASAR:
    Then she is well, and nothing on the other greatness,
    An 


##### Stretch Goal 
I used the Advance custom training to gain more control over my model by implementing a training loop by being given a starting point. 
We make this customizable look by using the tf.GradientTape to track the gradients. Ultimately, I preformed the model and calculated the lost function using the tf.GradientTape then compute updates and apply them with an optimizer. 
I decided to run the complete custom training loop which offered the most control and used 50 epochs on my model. Here are those results. 

    Epoch 1 Batch 0 Loss 1.1135
    Epoch 1 Batch 50 Loss 1.0837
    Epoch 1 Batch 100 Loss 1.1090
    Epoch 1 Batch 150 Loss 1.1401
    
    Epoch 1 Loss: 1.1307
    Time taken for 1 epoch 9.56 sec
    ________________________________________________________________________________
    Epoch 2 Batch 0 Loss 1.0827
    Epoch 2 Batch 50 Loss 1.0916
    Epoch 2 Batch 100 Loss 1.0930
    Epoch 2 Batch 150 Loss 1.1103
    
    Epoch 2 Loss: 1.0883
    Time taken for 1 epoch 9.55 sec
    ________________________________________________________________________________
    Epoch 3 Batch 0 Loss 0.9937
    Epoch 3 Batch 50 Loss 1.0314
    Epoch 3 Batch 100 Loss 1.0680
    Epoch 3 Batch 150 Loss 1.0574
    
    Epoch 3 Loss: 1.0432
    Time taken for 1 epoch 9.67 sec
    ________________________________________________________________________________
    Epoch 4 Batch 0 Loss 0.9458
    Epoch 4 Batch 50 Loss 0.9620
    Epoch 4 Batch 100 Loss 0.9843
    Epoch 4 Batch 150 Loss 1.0244
    
    Epoch 4 Loss: 0.9950
    Time taken for 1 epoch 9.71 sec
    ________________________________________________________________________________
    Epoch 5 Batch 0 Loss 0.8772
    Epoch 5 Batch 50 Loss 0.9139
    Epoch 5 Batch 100 Loss 0.9771
    Epoch 5 Batch 150 Loss 0.9945
    
    Epoch 5 Loss: 0.9448
    Time taken for 1 epoch 9.83 sec
    ________________________________________________________________________________
    Epoch 6 Batch 0 Loss 0.8646
    Epoch 6 Batch 50 Loss 0.8627
    Epoch 6 Batch 100 Loss 0.9294
    Epoch 6 Batch 150 Loss 0.9326
    
    Epoch 6 Loss: 0.8936
    Time taken for 1 epoch 9.73 sec
    ________________________________________________________________________________
    Epoch 7 Batch 0 Loss 0.7832
    Epoch 7 Batch 50 Loss 0.8116
    Epoch 7 Batch 100 Loss 0.8322
    Epoch 7 Batch 150 Loss 0.8754
    
    Epoch 7 Loss: 0.8404
    Time taken for 1 epoch 9.75 sec
    ________________________________________________________________________________
    Epoch 8 Batch 0 Loss 0.7576
    Epoch 8 Batch 50 Loss 0.7611
    Epoch 8 Batch 100 Loss 0.8007
    Epoch 8 Batch 150 Loss 0.8458
    
    Epoch 8 Loss: 0.7872
    Time taken for 1 epoch 9.77 sec
    ________________________________________________________________________________
    Epoch 9 Batch 0 Loss 0.7094
    Epoch 9 Batch 50 Loss 0.6956
    Epoch 9 Batch 100 Loss 0.7645
    Epoch 9 Batch 150 Loss 0.7797
    
    Epoch 9 Loss: 0.7374
    Time taken for 1 epoch 9.82 sec
    ________________________________________________________________________________
    Epoch 10 Batch 0 Loss 0.6500
    Epoch 10 Batch 50 Loss 0.6632
    Epoch 10 Batch 100 Loss 0.6963
    Epoch 10 Batch 150 Loss 0.7326
    
    Epoch 10 Loss: 0.6922
    Time taken for 1 epoch 10.02 sec
    ________________________________________________________________________________
    Epoch 11 Batch 0 Loss 0.5883
    Epoch 11 Batch 50 Loss 0.6111
    Epoch 11 Batch 100 Loss 0.6416
    Epoch 11 Batch 150 Loss 0.6929
    
    Epoch 11 Loss: 0.6506
    Time taken for 1 epoch 9.98 sec
    ________________________________________________________________________________
    Epoch 12 Batch 0 Loss 0.5597
    Epoch 12 Batch 50 Loss 0.5898
    Epoch 12 Batch 100 Loss 0.6237
    Epoch 12 Batch 150 Loss 0.6538
    
    Epoch 12 Loss: 0.6141
    Time taken for 1 epoch 9.95 sec
    ________________________________________________________________________________
    Epoch 13 Batch 0 Loss 0.5294
    Epoch 13 Batch 50 Loss 0.5511
    Epoch 13 Batch 100 Loss 0.5914
    Epoch 13 Batch 150 Loss 0.6313
    
    Epoch 13 Loss: 0.5833
    Time taken for 1 epoch 9.90 sec
    ________________________________________________________________________________
    Epoch 14 Batch 0 Loss 0.5073
    Epoch 14 Batch 50 Loss 0.5218
    Epoch 14 Batch 100 Loss 0.5599
    Epoch 14 Batch 150 Loss 0.6100
    
    Epoch 14 Loss: 0.5551
    Time taken for 1 epoch 9.94 sec
    ________________________________________________________________________________
    Epoch 15 Batch 0 Loss 0.4631
    Epoch 15 Batch 50 Loss 0.4899
    Epoch 15 Batch 100 Loss 0.5411
    Epoch 15 Batch 150 Loss 0.5979
    
    Epoch 15 Loss: 0.5324
    Time taken for 1 epoch 10.05 sec
    ________________________________________________________________________________
    Epoch 16 Batch 0 Loss 0.4749
    Epoch 16 Batch 50 Loss 0.4850
    Epoch 16 Batch 100 Loss 0.5179
    Epoch 16 Batch 150 Loss 0.5608
    
    Epoch 16 Loss: 0.5127
    Time taken for 1 epoch 10.00 sec
    ________________________________________________________________________________
    Epoch 17 Batch 0 Loss 0.4399
    Epoch 17 Batch 50 Loss 0.4837
    Epoch 17 Batch 100 Loss 0.4984
    Epoch 17 Batch 150 Loss 0.5318
    
    Epoch 17 Loss: 0.4989
    Time taken for 1 epoch 10.10 sec
    ________________________________________________________________________________
    Epoch 18 Batch 0 Loss 0.4263
    Epoch 18 Batch 50 Loss 0.4505
    Epoch 18 Batch 100 Loss 0.4851
    Epoch 18 Batch 150 Loss 0.5321
    
    Epoch 18 Loss: 0.4833
    Time taken for 1 epoch 10.10 sec
    ________________________________________________________________________________
    Epoch 19 Batch 0 Loss 0.4384
    Epoch 19 Batch 50 Loss 0.4483
    Epoch 19 Batch 100 Loss 0.4867
    Epoch 19 Batch 150 Loss 0.5278
    
    Epoch 19 Loss: 0.4710
    Time taken for 1 epoch 10.00 sec
    ________________________________________________________________________________
    Epoch 20 Batch 0 Loss 0.4026
    Epoch 20 Batch 50 Loss 0.4302
    Epoch 20 Batch 100 Loss 0.4481
    Epoch 20 Batch 150 Loss 0.5081
    
    Epoch 20 Loss: 0.4624
    Time taken for 1 epoch 10.12 sec
    ________________________________________________________________________________
    Epoch 21 Batch 0 Loss 0.4095
    Epoch 21 Batch 50 Loss 0.4381
    Epoch 21 Batch 100 Loss 0.4491
    Epoch 21 Batch 150 Loss 0.5088
    
    Epoch 21 Loss: 0.4560
    Time taken for 1 epoch 10.08 sec
    ________________________________________________________________________________
    Epoch 22 Batch 0 Loss 0.3924
    Epoch 22 Batch 50 Loss 0.4217
    Epoch 22 Batch 100 Loss 0.4509
    Epoch 22 Batch 150 Loss 0.5128
    
    Epoch 22 Loss: 0.4505
    Time taken for 1 epoch 10.11 sec
    ________________________________________________________________________________
    Epoch 23 Batch 0 Loss 0.4082
    Epoch 23 Batch 50 Loss 0.4258
    Epoch 23 Batch 100 Loss 0.4470
    Epoch 23 Batch 150 Loss 0.4855
    
    Epoch 23 Loss: 0.4452
    Time taken for 1 epoch 10.23 sec
    ________________________________________________________________________________
    Epoch 24 Batch 0 Loss 0.3986
    Epoch 24 Batch 50 Loss 0.4106
    Epoch 24 Batch 100 Loss 0.4522
    Epoch 24 Batch 150 Loss 0.4899
    
    Epoch 24 Loss: 0.4373
    Time taken for 1 epoch 10.24 sec
    ________________________________________________________________________________
    Epoch 25 Batch 0 Loss 0.3990
    Epoch 25 Batch 50 Loss 0.4031
    Epoch 25 Batch 100 Loss 0.4371
    Epoch 25 Batch 150 Loss 0.4681
    
    Epoch 25 Loss: 0.4302
    Time taken for 1 epoch 10.34 sec
    ________________________________________________________________________________
    Epoch 26 Batch 0 Loss 0.3912
    Epoch 26 Batch 50 Loss 0.3875
    Epoch 26 Batch 100 Loss 0.4425
    Epoch 26 Batch 150 Loss 0.4898
    
    Epoch 26 Loss: 0.4318
    Time taken for 1 epoch 10.26 sec
    ________________________________________________________________________________
    Epoch 27 Batch 0 Loss 0.3876
    Epoch 27 Batch 50 Loss 0.4062
    Epoch 27 Batch 100 Loss 0.4309
    Epoch 27 Batch 150 Loss 0.4525
    
    Epoch 27 Loss: 0.4248
    Time taken for 1 epoch 10.26 sec
    ________________________________________________________________________________
    Epoch 28 Batch 0 Loss 0.3923
    Epoch 28 Batch 50 Loss 0.3875
    Epoch 28 Batch 100 Loss 0.4313
    Epoch 28 Batch 150 Loss 0.4646
    
    Epoch 28 Loss: 0.4220
    Time taken for 1 epoch 10.25 sec
    ________________________________________________________________________________
    Epoch 29 Batch 0 Loss 0.3755
    Epoch 29 Batch 50 Loss 0.3907
    Epoch 29 Batch 100 Loss 0.4403
    Epoch 29 Batch 150 Loss 0.4620
    
    Epoch 29 Loss: 0.4200
    Time taken for 1 epoch 10.19 sec
    ________________________________________________________________________________
    Epoch 30 Batch 0 Loss 0.3608
    Epoch 30 Batch 50 Loss 0.3932
    Epoch 30 Batch 100 Loss 0.4196
    Epoch 30 Batch 150 Loss 0.4549
    
    Epoch 30 Loss: 0.4177
    Time taken for 1 epoch 10.27 sec
    ________________________________________________________________________________
    Epoch 31 Batch 0 Loss 0.3690
    Epoch 31 Batch 50 Loss 0.3889
    Epoch 31 Batch 100 Loss 0.4188
    Epoch 31 Batch 150 Loss 0.4574
    
    Epoch 31 Loss: 0.4165
    Time taken for 1 epoch 10.25 sec
    ________________________________________________________________________________
    Epoch 32 Batch 0 Loss 0.3846
    Epoch 32 Batch 50 Loss 0.3800
    Epoch 32 Batch 100 Loss 0.4283
    Epoch 32 Batch 150 Loss 0.4580
    
    Epoch 32 Loss: 0.4171
    Time taken for 1 epoch 10.18 sec
    ________________________________________________________________________________
    Epoch 33 Batch 0 Loss 0.3736
    Epoch 33 Batch 50 Loss 0.3855
    Epoch 33 Batch 100 Loss 0.4239
    Epoch 33 Batch 150 Loss 0.4758
    
    Epoch 33 Loss: 0.4196
    Time taken for 1 epoch 10.27 sec
    ________________________________________________________________________________
    Epoch 34 Batch 0 Loss 0.3794
    Epoch 34 Batch 50 Loss 0.3971
    Epoch 34 Batch 100 Loss 0.4267
    Epoch 34 Batch 150 Loss 0.4758
    
    Epoch 34 Loss: 0.4232
    Time taken for 1 epoch 10.29 sec
    ________________________________________________________________________________
    Epoch 35 Batch 0 Loss 0.3818
    Epoch 35 Batch 50 Loss 0.4083
    Epoch 35 Batch 100 Loss 0.4312
    Epoch 35 Batch 150 Loss 0.4623
    
    Epoch 35 Loss: 0.4233
    Time taken for 1 epoch 10.32 sec
    ________________________________________________________________________________
    Epoch 36 Batch 0 Loss 0.3812
    Epoch 36 Batch 50 Loss 0.3972
    Epoch 36 Batch 100 Loss 0.4277
    Epoch 36 Batch 150 Loss 0.4413
    
    Epoch 36 Loss: 0.4160
    Time taken for 1 epoch 10.26 sec
    ________________________________________________________________________________
    Epoch 37 Batch 0 Loss 0.3783
    Epoch 37 Batch 50 Loss 0.3766
    Epoch 37 Batch 100 Loss 0.4177
    Epoch 37 Batch 150 Loss 0.4508
    
    Epoch 37 Loss: 0.4109
    Time taken for 1 epoch 10.23 sec
    ________________________________________________________________________________
    Epoch 38 Batch 0 Loss 0.3519
    Epoch 38 Batch 50 Loss 0.3903
    Epoch 38 Batch 100 Loss 0.4325
    Epoch 38 Batch 150 Loss 0.4403
    
    Epoch 38 Loss: 0.4126
    Time taken for 1 epoch 10.25 sec
    ________________________________________________________________________________
    Epoch 39 Batch 0 Loss 0.3591
    Epoch 39 Batch 50 Loss 0.3816
    Epoch 39 Batch 100 Loss 0.4206
    Epoch 39 Batch 150 Loss 0.4740
    
    Epoch 39 Loss: 0.4188
    Time taken for 1 epoch 10.29 sec
    ________________________________________________________________________________
    Epoch 40 Batch 0 Loss 0.3974
    Epoch 40 Batch 50 Loss 0.3849
    Epoch 40 Batch 100 Loss 0.4303
    Epoch 40 Batch 150 Loss 0.4547
    
    Epoch 40 Loss: 0.4206
    Time taken for 1 epoch 10.40 sec
    ________________________________________________________________________________
    Epoch 41 Batch 0 Loss 0.3828
    Epoch 41 Batch 50 Loss 0.3922
    Epoch 41 Batch 100 Loss 0.4390
    Epoch 41 Batch 150 Loss 0.4454
    
    Epoch 41 Loss: 0.4182
    Time taken for 1 epoch 10.29 sec
    ________________________________________________________________________________
    Epoch 42 Batch 0 Loss 0.3740
    Epoch 42 Batch 50 Loss 0.3810
    Epoch 42 Batch 100 Loss 0.4255
    Epoch 42 Batch 150 Loss 0.4557
    
    Epoch 42 Loss: 0.4203
    Time taken for 1 epoch 10.23 sec
    ________________________________________________________________________________
    Epoch 43 Batch 0 Loss 0.3924
    Epoch 43 Batch 50 Loss 0.4032
    Epoch 43 Batch 100 Loss 0.4232
    Epoch 43 Batch 150 Loss 0.4652
    
    Epoch 43 Loss: 0.4269
    Time taken for 1 epoch 10.21 sec
    ________________________________________________________________________________
    Epoch 44 Batch 0 Loss 0.3974
    Epoch 44 Batch 50 Loss 0.4182
    Epoch 44 Batch 100 Loss 0.4255
    Epoch 44 Batch 150 Loss 0.4802
    
    Epoch 44 Loss: 0.4278
    Time taken for 1 epoch 10.20 sec
    ________________________________________________________________________________
    Epoch 45 Batch 0 Loss 0.3946
    Epoch 45 Batch 50 Loss 0.4109
    Epoch 45 Batch 100 Loss 0.4342
    Epoch 45 Batch 150 Loss 0.4755
    
    Epoch 45 Loss: 0.4287
    Time taken for 1 epoch 10.30 sec
    ________________________________________________________________________________
    Epoch 46 Batch 0 Loss 0.3743
    Epoch 46 Batch 50 Loss 0.3817
    Epoch 46 Batch 100 Loss 0.4277
    Epoch 46 Batch 150 Loss 0.4512
    
    Epoch 46 Loss: 0.4273
    Time taken for 1 epoch 10.33 sec
    ________________________________________________________________________________
    Epoch 47 Batch 0 Loss 0.3834
    Epoch 47 Batch 50 Loss 0.4289
    Epoch 47 Batch 100 Loss 0.4249
    Epoch 47 Batch 150 Loss 0.4664
    
    Epoch 47 Loss: 0.4303
    Time taken for 1 epoch 10.31 sec
    ________________________________________________________________________________
    Epoch 48 Batch 0 Loss 0.3715
    Epoch 48 Batch 50 Loss 0.4167
    Epoch 48 Batch 100 Loss 0.4352
    Epoch 48 Batch 150 Loss 0.4801
    
    Epoch 48 Loss: 0.4307
    Time taken for 1 epoch 10.21 sec
    ________________________________________________________________________________
    Epoch 49 Batch 0 Loss 0.3785
    Epoch 49 Batch 50 Loss 0.3947
    Epoch 49 Batch 100 Loss 0.4380
    Epoch 49 Batch 150 Loss 0.4623
    
    Epoch 49 Loss: 0.4311
    Time taken for 1 epoch 10.24 sec
    ________________________________________________________________________________
    Epoch 50 Batch 0 Loss 0.3931
    Epoch 50 Batch 50 Loss 0.4205
    Epoch 50 Batch 100 Loss 0.4537
    Epoch 50 Batch 150 Loss 0.4957
    
    Epoch 50 Loss: 0.4418
    Time taken for 1 epoch 10.31 sec