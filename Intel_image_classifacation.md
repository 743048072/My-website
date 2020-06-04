## Data Source and Description

The dataset we choose is from Kaggle (https://www.kaggle.com/puneet6060/intel-image-classification#20081.jpg), which contains around 25k colorful images of size 150x150. All the images are the natural scenes around the world and can be distributed under six classifications: Buildings, Forest, Glacier, Mountain, Sea, and Street.

All images have been separated into three folders, where 14k images in Train set, 3k in Test set, and 7k in Prediction set. Each folder has 6 sub-folders containing images of 6 classes. 
We randomly select 10 images from the training dataset and print them and their labels out as follows:

![Picture1](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture1.png)


## Data observation and issue

By looking at the images in our original dataset, we found that in some Building and Street images, the photo has included both building and street but some of them were classified into the Building and some of them were classified into the Street. The similar situation also happened on Glacier and Mountain. For instance, the following four pictures below (from left to right, picture 1,2,3,4) are representing Building, Street, Glacier, Mountain:

![picture8](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/picture8.png) 


## Methods
In this project we will use Convolutional Neural Network (CNN) and Transfer Learning with the VGG-16 model to make classification predictions. 

## Building CNN from scratch using Keras

A Convolutional Neural Network (ConvNet/CNN) is a Deep Learning algorithm which can take in an input image, assign importance (learnable weights and biases) to various aspects/objects in the image and be able to differentiate one from the other.  

### Model structure

Based on the classic CNN architecture, the CNN architecture we build is very similar. The model summary is as below.
 
![picture9](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/picture9.png)

The input image dimension in our dataset is 50*150*3. The element involved in carrying out the convolution operation in the first part of a Convolutional Layer is called the Kernel/Filter, K. For the first two ConvLayers, we have selected K as a 3x3x1 matrix and there are 32 kernels and we determine add one more ConvLayer after the second with 50 (3*3*1) kernels. The stride lengths are all 1.

The first layer is responsible for capturing the low-level features such as edges, color, gradient orientation and so on. With added layers, the architecture adapts to the high-level features as well, giving us a network which has the wholesome understanding of images in the dataset.

After convolutional layers, we add a max pooling layer to return the maximum value from the portion of the image covered by the Kernel. The max pooling layer and the convolutional layer, together form the i-th layer of a CNN. Depending on the complexities in the images, we use 2 such layers for capturing low-level details even further, but at the cost of more computational power. 

Finally, we use fully connected layers to learn non-linear combinations of the high-level features as represented by the output of the convolutional layer. We have converted our data into a suitable form for our multi-level perceptron and flattened the image into a column vector. The flattened output is fed to a feed-forward neural network and backpropagation applied to every iteration of training.

### Model compilation

The compilation is the final step in creating a model. In our model, loss function is used to find error or deviation in the learning process. We use “sparse_categorical_crossentropy” for our loss function and “Adam” function with learning rate 0.0001 for optimizer.

In the training process, we tried epoach 5 and 10 for training to save our time for seeing the result. However, the accuracy with such epoch is pretty low, with around 50%. So we plot the relationship between accuracy and epoch to what epoch shall we
choose. As a result, we found that after 14 epochs, the accuracy reaches almost the highest level and goes up very slightly. 

![Picture3](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture3.png)

![Picture4](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture4.png)

So we decided to use epoch 14, to ensure the highest accuracy and lowest loss. The training and testing accuracies are as follows:

Training accuracy:
14034/14034 [==============================] - loss: 0.4410 - accuracy: 0.9087

Testing accuracy:
3000/3000 [==============================] - loss: 0.5784 - accuracy: 0.8030
 
 
## Transfer learning with VGG-16 using Keras

Conventional machine learning and deep learning algorithms have been traditionally designed to work in isolation. These algorithms are trained to solve specific tasks. The models have to be rebuilt from scratch once the feature-space distribution changes. Transfer learning is the idea of overcoming the isolated learning paradigm and utilizing knowledge acquired for one task to solve related ones.

One of the fundamental requirements for transfer learning is the presence of Pre-trained models that perform well on source tasks. Pre-trained models are usually shared in the form of the millions of parameters/weights the model achieved while being trained to a stable state.  

The pre-trained CNN model that we will be using is the popular VGG-16 model, which has learned a good representation of features for over a million images belonging to 1,000 different categories can act as a good feature extractor for new images suitable for computer vision problems. 

![Picture5](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture5.png)
 
You can clearly see that we have a total of 13 convolution layers using 3 x 3 convolution filters along with max pooling layers for downsampling and a total of two fully connected hidden layers of 4096 units in each layer followed by a dense layer of 1000 units, where each unit represents one of the image categories in the ImageNet database.

We do not need the last three layers since we will be using our own fully connected dense layers for the classification of our data. Thus, we are going to leverage the convolution blocks of the VGG-16 model and then flattening the final output so that we can feed it into our own dense layers for our classifier.

Keras provides an interface to download the VGG-16 model. We can just import VGG16 from tensorflow.keras.applications.
When loading up the VGG-16 model, we freeze the convolution blocks by setting weights='imagenet' (pre-training on ImageNet), because we don’t want their weights to change during model training, so that we can use it as just an image feature extractor.

We also set include_top=False meaning we don’t want to include the 3 fully-connected layers at the top of the network.
In Keras, each layer has a parameter called “trainable”. For freezing the weights of convolution blocks, we should set this parameter to False, indicating that this should not be trained.

In the next step, we can instantiate the sequential model and add convolution blocks of VGG-16 to the beginning of the model, and then add a flatten layer and dense layers so as to feed the convolution blocks to a customized fully connected deep neural network classifier.

After building the CNN model, what we should do is just compiling and fitting the model as what we did before.

![Picture6](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture6.png)

After compiling and fitting the model for 3 epochs, we get a CNN model of overall training accuracy of 93.43% and testing accuracy of 91.1%.

Training accuracy:
14034/14034 [==============================] - loss: 0.1846 - accuracy: 0.9343

Testing accuracy:
3000/3000 [==============================] - loss: 0.2831 - accuracy: 0.9110


## Transfer learning with VGG-16 using PyTorch

![Picture7](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture7.png)

## Conclusion  

[back](https://github.com/743048072/Wendy-Zhai/)
