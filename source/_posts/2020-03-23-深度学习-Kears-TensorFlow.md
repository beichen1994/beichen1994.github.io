---
title: 深度学习-Kears+TensorFlow
date: 2020-03-23 14:43:45
tags:
- neural network and deep learning
categories: 
- Computer
---


Tensorflow: 作为google主推的深度学习框架，未来支持会更好

Keras：跨平台兼容，后台Tensorflow/Theano均可，可以直接当黑箱使用，速度稍慢，隐藏了很多内部参数

Keras+Tensorflow组合：以Keras为主，用tensorflow语句来写扩展功能并和Keras结合使用。

Tensorflow安装：

* CPU版本: pip3 install --upgrade tensorflow
* GPU版本: pip3 install --upgrade tensorflow-gpu，需要进一步安装CUDA和cuDNN。

Keras安装:

* 依赖包：numpy，scipy，pyyaml，HDF5，h5py，如果拟合CNN（卷积神经网络），推荐安装cuDNN。

* 后端框架：Tensorflow

* pip install keras -U --pre