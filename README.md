# Image Captioning

## Introduction
Image Captioning is the process of generating a textual description for given images.
Image captioning can be regarded as an end-to-end Sequence to Sequence problem, as it converts images, which is regarded as a sequence of pixels to a sequence of words.
Image captioning has a huge amount of application

## Applications of Image Captioning
* Recommendations in Editing Applications
* Assistance for Visually Impaired
* Social Media Posts Analysis and Actions

## Methodology
The custom word embedding is used to encode the words. These
embeddings are also adjusted during the training phase. The embedding layer is followed by the network which is explained below.

The attention mechanism is present at various levels. First, the objects are detected with in the image using a suitable object detector. Parallelly the image is passed through several convolution layers. In the next step one global attention is applied to the CNN outputs and local attention is given to one or more objects at a time. The outputs of the two LSTM layers are combined (concatenate) and final output is predicted.

Policy based loss function is used. The loss function is masked with a mask that has zero entries whenever actual output contains a zero. Apart, from this there is a discriminator also. Which consists of two LSTM layers and dense, dropout layers following them which finally give one output.

This discriminator provides Adversial training to the generator network. This discriminator and the generator both improve as the training progresses.

Cross entropy loss function is used to calculate the loss. Adam optimizer is used while training the network. The hyperparameters for the optimizer are unchanged except for the learning rate. We have used a fairly high learning rate of $10^{-4}$, which is unusual in NLP tasks.

For generating the caption on the test set, random word is selected from  the distribution. No sooner the $<end>$ token is received the process stops  otherwise the predicted word is tokenized and feed into the RNN.

The rest of the script involves pre-processing and other minor but  significant operation as required by the system. Pre-processing involves resizing the images to proper size, and tokenizing the word, removing punctuations, etc. The CNN network uses the ResNet architecture.

### Encoding
The words are first tokenized.
The custom trainable encoding is used.
Two convolutional networks are used to extract global and local features of images.


### Novelty
The model has used GAN and attention mechanisms both spatial and local together in one model.
All these combined can be attributed to the success of model.

## Dataset
There are two datasets popular for image captioning task namely, MS COCO dataset and Flickr dataset.
Our primary dataset is MS COCO because it is readily available and can be downloaded even in run time.
MS COCO has 330 thousand images and at least 5 captions for each image.


## FutureWork
1. Pre trained models for the embeddings can be incorporated to better model the words and improve the meaningfulness of the system. Glove embedding is one of popular embeddings trained on blogs.
2. Beam search can be used to model the grammar for generating the captions instead of one random word out of distribution.