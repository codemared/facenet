# Rolex Reference Recognition using Tensorflow-keras [![Build Status][travis-image]][travis]

[travis-image]: http://travis-ci.org/davidsandberg/facenet.svg?branch=master
[travis]: http://travis-ci.org/davidsandberg/facenet

This is a TensorFlow implementation of the face recognizer described in the paper
["FaceNet: A Unified Embedding for Face Recognition and Clustering"](http://arxiv.org/abs/1503.03832). The project also uses ideas from the paper ["Deep Face Recognition: A survey"](https://arxiv.org/pdf/1804.06655.pdf), ["DEEP METRIC LEARNING USING TRIPLET NETWORK"](https://arxiv.org/pdf/1412.6622.pdf), ["How to Train Triplet Networks with 100K Identities?"](https://arxiv.org/pdf/1709.02940.pdf)

## Compatibility
The code is tested using Tensorflow 1.12.0 and keras 2.2.4 under Ubuntu 18.04 with Python 3.6.


## Pre-trained models
| Model name      | accuracy | Training dataset | Architecture |
|-----------------|--------------|------------------|-------------|
| [20180408-102900](https://drive.google.com/open?id=1R77HmFADxe87GmoLwzfgMu_HY0IhcyBz) | 0.4934034        | Rolex Wrist Watch    | [Resnet50](https://github.com/davidsandberg/facenet/blob/master/src/models/inception_resnet_v1.py) |


## Inspiration
The code is heavily inspired by the [Face recognition](https://github.com/mjDelta/face-recognition-keras) implementation.

## How to use

To install all the requirements for the project run

	pip install -r requirements.txt

In the root directory. After the modules have been installed you can train the model by using python

	python3 train.py

## Training data
The [Rolex Wrist Watch](https://drive.google.com/file/d/14h6HSvRvcmU3tfWccJflhZngLb_5GdUl/view) dataset has been used for training. This training set consists of total of nearly 13k images over 697 identities of Rolex watch. A csv file [Rolex CSV] which contains all the IDs of the Rolex images and References of the Rolex watch.

## Running training
Currently, the best results are achieved by training the model using softmax loss. Details on how to train a model using softmax loss on the CASIA-WebFace dataset can be found on the page [Classifier training of Inception-ResNet-v1](https://github.com/davidsandberg/facenet/wiki/Classifier-training-of-inception-resnet-v1) and .

## Performance
At first we try to visualize the Rolex dataset in t-sne for 32 categories using ResNet50 pretrained model. visualizing graph is given bellow:

And then apply triplet net on top of ResNet50 pretrained model for 32 categories. we found some impressive performance which is given bellow:

Finally we try to work with those categories of the Rolex watch which have at least 10 samples without oversampling but could not complete the training. After few ours training we found nearly 50% accuracy. 

## Farther performance improvement
There are lots of scope for improvement. First of all, using oversampling or increase the number of samples in the categories which have less samples. We couldn't train our model for enough time, if the training period lasts long the model may learn more.  And lastly, we applied knn algorithms for classification but cosFace technique may work well in this case.
