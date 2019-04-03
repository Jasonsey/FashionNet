# FashionNet 

> the code of the paper, FashionNet. using keras, on jupyter
>
> using the data set of the FashionNet's subset, in-shop_clothes_retrieval_benchmark

## Project Structure

```shell
├── data                                      # all input and output data are saved here 
│   ├── input -> /data/DeepFashion/in-shop_clothes_retrieval_benchmark    # input data
│   └── output                                # output data
├── src                                       # source code
│   ├── DatasetPreprocessing.ipynb            # data set preprocessing code
│   └── FashionNet.ipynb                      # FashionNet code
└── README.md
```

## Reproduction Statement

1. Preprocessing code has been completed (In DatasetPreprocessing.ipynb).

2. Data set reading code of model training has been completed (In FashionNet.ipynb).

3. The code of model structure has been completed (In FashionNet.ipynb).

4. The code for model predicting has not been completed.

## FashionNet Introduction

FashionNet is used to predict landmarks, category, attribute in clothing images. And its network structure is as follows.

The network structure consists of three parts, blue, red, and green. And they use the same base model, the first 4 layers of VGG16 pretrained on imagenet data set.

![](https://ws1.sinaimg.cn/mw690/006ztUIbgy1g1ktb2xr5sj30qk0rwjzr.jpg)


### Blue part

The blue part of FashionNet is used to predict the landmarks location and landmark visibility. It's exactly the same as the VGG16 backend network, except for the ouput layer

### Red part

The red part of FashionNet is used to generate the global features of images. It's the same as the conv4 and first dense layer of VGG16.

### Green part

The green part of FashionNet is used to generate the local features near landmarks of images. 

1. pool5_local: the same as ROI pooling. And the ROI is generated from imaages near landmarks

### Concatenation of red and green part

We simply concatenate the green and red part for attribute, category and triplet prediction.

## Q&A

### How to download the FashionNet data set

You can download the dataset from [All FashionNet Dataset](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion.html)

![img](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion/retrieval_consumer2shop.png)

### How to train FashionNet

Don't worry, I've commented on the code in detail. If you encounter any training problem, please feel free to contact me.

### How to use FashionNet

Since time limited, the prediction code has not been implemented. Maybe I'll finish it later.

After all, if you want to predict the landmarks or category of the clothing images, just use the blue part. And if you want to predict the attribute or category of the clothing images, just use the red and green part.