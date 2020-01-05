# Generative-adverserial-Networks-Face-profile-completion


This project pertains to using Deep learning model like adverserial networks(2 CNN neural networks) compete against each other
, One to generate fake images(generator) , other to defy it(discriminator). 

Objective: Given the profile of a person , can we generate the entire face structure. 

1) Infrastructure: Figure out how to set up Google Cloud ML instance utilising the $300 credits.
2) Code : Segmented into 
  2.1) Data.py ( How to get data onto the GCP platform )
  2.2) Network.py ( Setting up the CNN's for generation and discrimination )
  2.3) Main.py ( Running 500 epochs and taking the model evaluation paramater as L1, L2 and Binary cross entropy(as our results are binary in nature)
  2.4) test.py ( To test our model over the test images )
  
3) Dataset: Getting facial datasets with side and frontal
	3.1) Manual pre-processing of images to required dimensions
	3.2) Tagging (pairing) of side and frontal as training set
