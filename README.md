# Generative-adverserial-Networks-Face-profile-completion


This project pertains to using Deep learning model like adverserial networks(2 CNN neural networks) compete against each other
, One to generate fake images(generator) , other to defy it(discriminator). 

### Objective: Given the profile of a person , can we generate the entire face structure. 

1) Infrastructure: Figure out how to set up Google Cloud ML instance utilising the $300 credits.
2) Code : Segmented into 
  2.1) Data.py ( How to get data onto the GCP platform )
  2.2) Network.py ( Setting up the CNN's for generation and discrimination )
  2.3) Main.py ( Running 500 epochs and taking the model evaluation paramater as L1, L2 and Binary cross entropy(as our results are binary in nature)
  2.4) test.py ( To test our model over the test images )
  
3) Dataset: Getting facial datasets with side and frontal (training data obtained from CMU Multi-pie Face Dataset)
	3.1) Manual pre-processing of images to required dimensions
	3.2) Tagging (pairing) of side and frontal as training set

Check the 499_real, 499_input , 499_generated for the accuracy achieved. 

## A bit of Theory for the concept:
there are two main concepts that we will need for the face Frontalization:

1) The Encoder/Decoder Network
2) The Generative Adversarial Network

Encoders and Decoders
The Encoder

The network takes images that are sized 128 by 128 as input. Since the images are in colour (meaning 3 colour channels for each pixel), this results in the input being 3 × 128 × 128 = 49152 dimensional. We can get away with a mere 512 dimensional vector (which is simply another way of saying “512 numbers”) to encode all the information that we care about. This is an example of dimensionality reduction: the Encoder network learns a lower dimensional representation of the input. 

Here we start with input that is 128×128 and has 3 channels. As we pass it through convolutional layers, the size of the input gets smaller and smaller (from 128×128 to 64×64 to 16×16 etc on the figure above) whereas the number of channels grows (from 3 to 8 to 16 and so on). This reflects the fact that the deeper the convolutional layer, the more abstract are the features that it learns. In the end we get to a layer whose output is sized 1×1, yet has a very high number of channels: 256 in the example depicted above (or 512 in our own network). 256×1 and 1×256 are really the same thing, if you think about it, so another way to put it is that the output of the Encoder is 256 dimensional (with a single channel), so we have reduced the dimensionality of the original input from 49152 to 256. Having this lower dimensional representation helps us prevent overfitting our final model to the training set.

The Decoder

As the name suggests, the Decoder’s job is the inverse of that of the Encoder. In other words, it takes the low-dimensional representation output of the Encoder and has it go through deconvolutional layers (also known as the transposed convolutional layers). The architecture of the Decoder network is often symmetric to that of the Encoder, although this does not have to be the case. The Encoder and the Decoder are often combined into a single network.

In this project this Encoder/Decoder network is called the Generator. The Generator takes in a profile image, and (if we do our job right) outputs a frontal one.
