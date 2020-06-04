## Data Source and Description

The dataset we choose is from Kaggle, which contains around 25k colorful images of size 150x150. All the images are the natural scenes around the world and can be distributed under six classifications: Buildings, Forest, Glacier, Mountain, Sea, and Street.

All images have been separated into three folders, where 14k images in Train set, 3k in Test set, and 7k in Prediction set. Each folder has 6 sub-folders containing images of 6 classes. (https://www.kaggle.com/puneet6060/intel-image-classification#20081.jpg)

We randomly select 10 images from the training dataset and print them and their labels out as follows:

![Picture1](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture1.png)

## Data observation and issue

By looking at the images in our original dataset, we found that in some Building and Street images, the photo has included both building and street but some of them were classified into the Building and some of them were classified into the Street. The similar situation also happened on Glacier and Mountain. For instance, the following four pictures below (from left to right, picture 1,2,3,4) are representing Building, Street, Glacier, Mountain:

![Picture%208](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture%208.png) 



![Picture5](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture5.png)
![Picture6](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture6.png)

![Picture%208](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture%208.png)
![Picture%209](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture%209.png)

## Building CNN from scratch using Keras

![Picture%209](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture%209.png)

![Picture3](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture3.png)

![Picture4](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture4.png)

## Transfer learning with VGG-16 using Keras

![Picture5](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture5.png)
![Picture6](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture6.png)

## Transfer learning with VGG-16 using PyTorch

![Picture7](https://github.com/743048072/Wendy-Zhai/blob/master/assets/Intel/Picture7.png)

## Conclusion  

[back](https://github.com/743048072/Wendy-Zhai/)
