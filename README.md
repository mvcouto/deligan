# DeLiGAN

  This project is an implementation of the Generative Adversarial Network proposed in our CVPR 2017 paper - DeLiGAN : Generative Adversarial Networks for Diverse and Limited Data. DeLiGAN is a simple but effective modification of the GAN framework and aims to improve performance on datasets which are diverse yet small in size. 

## Dependencies

  The code for DeLiGAN is provided in Tensorflow 0.10 for the MNIST and Toy dataset, and in Theano 0.8.2 + Lasagne 0.2 for the CIFAR-10 and Sketches dataset. This code was tested on a Ubuntu 14.04 workstation hosting a NVIDIA Titan X GPU. 
  
## Datasets

  This repository includes implementations for 4 different datasets. 
   1. Toy (self generated unimodal and bimodal gaussians)
   2. MNIST (http://www.cs.toronto.edu/~gdahl/mnist.npz.gz)
   3. CIFAR-10 (https://www.cs.toronto.edu/~kriz/cifar.html)
   4. Sketches (http://cybertron.cg.tu-berlin.de/eitz/projects/classifysketch/)

The models for evaluating DeLiGAN on these datasets can be found in our repo. The details for how to download and lay out the datasets can be found in src/datasets/README.md 

## Usage

### Training DeLiGAN models

  To run any of the models
   - First download the datasets and store them in the respective sub-folder of the datasets folder (src/datasets/) 
   - To run the model on any of the datasets, go to the respective src folders and run the dg_'dataset'.py file in the respective dataset folders with two arguments namely, --data_dir and --results_dir. For example, starting from the top-level folder, cd src/sketches ; python dg_sketches.py --data_dir ../datasets/sketches/ --results_dir ../results/sketches
   - Note that the results_dir needs to have 'train' as a sub-folder.

### Modified inception score  
For example, to obtain the modified inception scores on CIFAR
   - Download the inception-v3 model (http://download.tensorflow.org/models/image/imagenet/inception-2015-12-05.tgz.) and store it in src/modified \inception \scores/cifar10/
   - Generate samples using the model trained in the dg_cifar.py and copy it to src/modified_inception_scores/cifar10/
   - Run transfer_cifar10_softmax_b1.py to transfer learn the last layer.
   - Perform the modifications detailed in the comments in transfer_cifar10_softmax_b1.py and re-run it to evaluate the inception scores.
   - The provided code can be modified slightly to work for sketches as well by following the comments provided in transfer_cifar10_softmax_b1.py
   
Parts of the code in this implementation have been borrowed from the Improved-GAN implementation by OpenAI (T. Salimans, I. Goodfellow, W. Zaremba, V. Cheung, A. Radford, and X. Chen. Improved techniques for training gans. In Advances in Neural Information Processing Systems, pages 2226–2234, 2016.)

## Q&A

Please send message to gauthamsindia95@gmail.com if you have any query regarding the code.