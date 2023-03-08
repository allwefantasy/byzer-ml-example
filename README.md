# Byzer Machine Learning Examples

## 1. Introduction

This repository contains the examples of Byzer Machine Learning. And all these examples are developed by Byzer Desktop.

## 2. How to use

before you use these examples, you need to install Byzer Desktop. Please refer to [Byzer Desktop Installation Guide](https://zhuanlan.zhihu.com/p/603399058). If you have installed Byzer Desktop before, please make sure the version of Byzer Desktop plugin >=0.9.0 (or reinstall Byzer Desktop according to the guide)

### 2.1. simple-ml.mlsqlnb

In this example, we will use Byzer to train a simple machine learning model without any python language skill. We will use the [Iris dataset](https://archive.ics.uci.edu/ml/datasets/iris) to train a model to predict the species of an Iris flower based on its sepal and petal measurements. Once the model is trained, we will use register the mode as UDF so you can  predict the species of an Iris flower in SQL.

### 2.2. sklearn.mlsqlnb

In this notebook, we will show youin Byzer how to:

1. train sklearn model  
2. deploy the model as UDF 
3. use the UDF in SQL

