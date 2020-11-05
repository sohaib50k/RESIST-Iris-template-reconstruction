# RESIST-Iris-template-reconstruction
Reconstructing irises from deep templates. 

For starters the implementation uses Keras and Tensorflow, other needed packages include numpy, opencv, matplotlib among others. Spectral normalization and instance normalization are used to better train the RESIST GAN. Files for both Spectral normalization and instance normalization are added.


# Training process 
RESIST takes feature vectors as inputs and outputs reconstructed iris images. The feature vector extraction process begins with iris segmentation. The [segmentation pipeline](https://github.com/sohaib50k/Unconstrained-iris-segmentation-using-Mask-R-CNN) is available on Github. The segmentation pipeline outputs square segmented iris images with the background set to black. These segmented images are fed to the [recognition pipeline] called ThirdEye. The code for the recognition pipeline is available in this repository. RESIST uses a custom Keras generator to load data. The data format is as follows:

* Training data
  * Image folder
    * iris_image1
    * iris_image2
  * Feature vector folder
    * feature_vector1
    * feature_vector2
    
Iris inversion process using RESIST is a class agnostic process however the segmentation and recognition pipeline are implemented for the Notre Dame 0405 dataset which has the following filename type: 02463d834l.png where 02463 is the class and 834 is the image and 'l' denotes the left iris.

# Testing process

When the model is trained to completion it reads a test folder containing feature vectors in the same format as the training dataset. It then outputs reconstructed irises into a separate folder.

Some sample reconstructed images from the paper:

![Reconstructed iris images](https://i.ibb.co/VHzjr3w/Picture1.png)


If you use this repository consider citing our [papers](https://arxiv.org/pdf/2007.15850.pdf)

@article{ahmad2020resist,
  title={Resist: Reconstruction of irises from templates},
  author={Ahmad, Sohaib and Fuller, Benjamin},
  journal={arXiv preprint arXiv:2007.15850},
  year={2020}
}

[Recognition paper](https://ieeexplore.ieee.org/abstract/document/9185998)

@INPROCEEDINGS{9185998,author={S. {Ahmad} and B. {Fuller}},
booktitle={2019 IEEE 10th International Conference on Biometrics Theory, Applications and Systems (BTAS)},
title={ThirdEye: Triplet Based Iris Recognition without Normalization},
year={2019},
volume={},
number={},
pages={1-9},
doi={10.1109/BTAS46853.2019.9185998}}

