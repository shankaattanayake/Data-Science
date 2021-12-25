# FashionMNIST Random Forest Classifier

# Introduction

In this project we wanted to benchmark and understand the performance of Random Forest Classifier on the FashionMNIST image classification task. Random Forest Classifier is a generic classification algorithm which enforces minimal constraints on the input format for features. In our experiments we show that a Random Forest Classifier can reach an accuracy which is comparable to deep learning models. We also perform experiments to understand the importance of different data augmentation techniques.

Interpreting the decision process of a machine learning model is important to build trust in deployed models. In this work we also show how one can interpret the decision process of a Random Forest Classifier, a functionality which is absent in today&#39;s deep learning models.


# Dataset

We conduct experiments on the FashionMNIST dataset ([https://arxiv.org/abs/1708.07747](https://arxiv.org/abs/1708.07747)). It is a dataset of [Zalando](https://jobs.zalando.com/tech/)&#39;s article images and consists of a training set of 60,000 images and a test set of 10,000 images. Each image is a 28x28 grayscale image, associated with a label from 10 classes. The images are in grayscale. Every single pixel is represented by a number in a range from 0 to 255 where 0 corresponds to black color and 255 corresponds to white.

![image](https://github.com/shankaattanayake/Data-Science/blob/main/Machine%20Learning%201%20Algorithm/Fashion-Mnist%20Project/Images/Aspose.Words.fb87694c-b2b9-4304-b9c5-2639d593cf81.001.png)<br >

Fig-1: Categories in the FashionMNIST dataset, [0 Tshirt/top, 1 Trouser, 2 Pullover, 3

Dress, 4 Coat, 5 Sandal, 6 Shirt, 7 Sneaker, 8 Bag, 9 Ankle boot].


# DataAugmentation

The quality of machine learning models that we train is highly dependent on both the quality and amount of data that we use for training the model. Data Augmentation is a strategy using which we can both increase the amount of data that we use for training the model and also make our model robust to variation in data distribution.

Data Augmentation is an important component of the machine learning pipeline for computer vision tasks because in computer vision we feed images as input to machine learning models. What image is captured is highly dependent on the camera configuration and placement.Forexampleitisquitelikelythattwodifferentpeoplewillcapturedifferentlooking images of the same object, there can be a variation in the rotation, positioning of the object in the image. We want our computer vision machine learning models to be robust to these changes, to achieve this we tried to train our RandomForestClassifier with different data augmentation strategies.

- Horizontal/VerticalFlips
- Copy-paste

![image](https://github.com/shankaattanayake/Data-Science/blob/main/Machine%20Learning%201%20Algorithm/Fashion-Mnist%20Project/Images/Aspose.Words.fb87694c-b2b9-4304-b9c5-2639d593cf81.002.png)<br >

Fig-2: Data augmentation techniques for FashionMNIST dataset.


# Modeling

We train a random forest classifier for learning to classify the Fashion MNIST image. A random forest classifier trains multiple decision tree. Features picked for randomly partitioning the training dataset are independent across each decision tree trained in the ensemble. For test time inference predictions from the different decisions trees are aggregated to come up with the final predictions.

  
## Random Forest Classifier forImages

Random Forest Classifiers are a generic classification algorithm which only require a canonical input data representation (array of features, label). Recent progress in deep learning has seen the application of convolutional neural nets (CNN) to images. CNNs architecture leverages translational and rotational invariance of images to learn features which are then input to a linear layer for classification. In this work we wanted to test the performance of Random Forest Classifier on images.

![image](https://github.com/shankaattanayake/Data-Science/blob/main/Machine%20Learning%201%20Algorithm/Fashion-Mnist%20Project/Images/Aspose.Words.fb87694c-b2b9-4304-b9c5-2639d593cf81.003.png)<br >

Fig-3: treeviz visualization for a single decision tree in a FashionMNIST Random Forest Classifier. The visualization was generated using the treeviz library ([https://github.com/PierreCapo/treeviz](https://github.com/PierreCapo/treeviz)).

Fig-3 showcases how a single decision tree is trained in a random forest classifier on the FashionMNIST dataset. We will walk through the left-most path in the decision tree to better explain the modeling process. Each image in the FashionMNIST dataset consists of 28x28 = 784 pixels. Each pixel is passed in as a unique feature to the decision tree. There are 784 total features (px1, px2, …, px784). At the root node px100 is selected as the partition feature. The top most diagram in Fig-3 shows a histogram for px100 for the different images. To simplify the visualization we randomly selected 1000 out of the total 60,000 training images for this diagram. To partition the train set at the root node a threshold of 0.50 is selected by the decision tree, images with px100 value less than equal to 0.5 are sent to the left node and images with px100 greater than 0.5 are sent to the right node. This process continues until we reach the left node. Here for simplicity we have limited the max depth in the decision tree to 3. If we observe the left-most leaf node we see that the class &quot;Sandal&quot; and &quot;Sneaker&quot; have been clustered together. Intuitively this is expected as in terms of appearance sandals and sneakers are relatively close compared to other pair of classes as both are examples of a footwear.


# Experiments andResults

In our experiments we observed that dataset augmentation techniques were important in ensuring the robustness of Random Forest Classifier. Last row in Table-1 shows that a model trained on the standard FashionMNIST training dataset achieves only 61.1% accuracy when tested on a dataset containing horizontally and vertically flipped images. Our remaining experiments show that adding in data augmentation strategies recovers the performance. This observation shows that for ensuring the robustness of Random Forest Classifier models it is important to add augmentation strategies in the training dataset.

| N-Estimators | 50 | 100 | 200 | 500 |
| --- | --- | --- | --- | --- |
| Data Augmentation on Training &amp; Test | 86.8% | 87.2% | 87.2% | 87.4% |
| Scaling + Data Augmentation on Training &amp; Test | 86.9% | 87.1% | 87.3% | 87.4% |
| Normalization + Data Augmentation on Training &amp; Test | 86.7% | 87.1% | 87.2% | 87.4% |
| Scaling + Normalization + Data Augmentation on Training &amp; Test | 86.8% | 87.4% | 87.4% | 87.4% |
| Training Data Without Data Augmentation | 61.1% | 61.1% | 60.9% | 61.4% |

Table-1: data augmentation and N Estimators experiments. The model without data augmentationshowspoorperformanceonthetestdatasetwhichconsistsofhorizontallyand vertically flipped images(row-5).

![image](https://github.com/shankaattanayake/Data-Science/blob/main/Machine%20Learning%201%20Algorithm/Fashion-Mnist%20Project/Images/twoconfusionmatrixes.PNG)<br >



  
## N-Estimators

Table-1 reports the performance for different settings of N Estimators. The N Estimators parameter increased the accuracy by 0.6%. Four different N Estimator values were used: 50,100,200,500 in our hyperparameter search experiments. The improvement in accuracy was minimal from 50 to 100, but it was higher than the accuracy improvements between 100 to 500.

  
## Scaling andNormalization

Table-1 reports that scaling and normalization data pre-processing had a small effect on performance. This observation shows that scaling and normalization has minimal impact on model performance if all the features are roughly in the same range. In the case of images each pixel can only take integer values in the interval [0, 255].

  
## Best Performing ModelConfiguration

In our experiments we show that best performing random forest classifier configuration consists of scaling, normalization data pre-processing, horizontal and vertical flip data augmentation and N-Estimators equal to 100. This model achieves 87.4% performance on the FashionMNIST test dataset. This performance is comparable to Vanilla CNNs as reported in the README of the FashionMNIST repository ([https://github.com/zalandoresearch/fashion-mnist](https://github.com/zalandoresearch/fashion-mnist))whichachievecloseto90%performance on the testsplit.

  
## Analysis

The confusion matrix of the best model can be seen in Fig-6. From the confusion Matrix, it is evident that the model is capable of accurately distinguishing between different categories of data, such as between tops (category-1), sneakers (category-8) and bottoms (category-2).

The confusion matrix also gives us an insight into categories which are tough for the model to distinguish, e.g. shirt (category-7) and coat (category-5), T-shirt/top (category-1) and pullover (category-3). Fig-6 shows the corresponding mistakes made for the pairs of these categories, e.g. T-shirt/top (category-1) gets confused with pullover (category-3) over 100 times on the test set.

![image](https://github.com/shankaattanayake/Data-Science/blob/main/Machine%20Learning%201%20Algorithm/Fashion-Mnist%20Project/Images/Aspose.Words.fb87694c-b2b9-4304-b9c5-2639d593cf81.006.jpeg)<br >

Fig-6: Confusion matrix for the best model configuration.


# Conclusion

In summary, the key problem was detected and addressed however, it had underlying small challenges that put into test what was the best alternative to pick to reach a model accuracy superior to 80%. Thanks to some techniques such as scaling, standardization, and data augmentation, the algorithm performance started to improve since the different rotations applied to the images transformed a 60k training set into a 180k training set as a result of which the model had more data to fit. With the different augmentations we reached an 87.4% accuracy for a Random Forest Classifier.

