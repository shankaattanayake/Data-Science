### Project ASL Sign Detection.

## Problem Statement
Design a model trained to learn human features gestures for signed interpretations by predictingand classifying American Sign Language without the help of a physical translator.

## Dataset

The dataset was picked from kagglehttps://www.kaggle.com/bsashank/asl-recognitionwhichconsists of hand gestures depicting the alphabets from American Sign language, divided into 26folders which represent the different classes. The 26 classes consists of 26 letters of the Englishalphabet.The dataset has 1584 images. The images were already annotated. The data was split into trainand test files respectively.

## Data Augmentation
| ![ezgif com-gif-maker (4)](https://github.com/shankaattanayake/Data-Science/blob/main/Deep_Learning/ASL_Translator/Video/ezgif.com-gif-maker%20(2).gif) |
In an attempt to increase the number of images per class, RoboFlow was used for DataAugmentation. After using the data augmentation function in RoboFlow, most classes had morethan 100 images and the dataset was increased from 1573 images to 3828 images.  The DataAugmentation performed were rotating images within 45 degrees and flipping on the verticalAxis.

## YOLOV5

The YOLOV5 model was trained for 150 epochs at a batch size of 2. Initially, the training was meant to be completed using Google Colab, but it was rendered useless as Google Colab keptcrashing close to the midpoint of training. Next, training on a local computer was used. Trainingon a local computer took 2 full days. The results from the training can be seen in Figure: EpochsVs Training Metrics. During the training, it can be seen that the Precision, Recall and MeanAverage Precision at 0.5 and 0.5 to 0.95  have stabilized close to 100 epochs and after 100epochs it seems that the model is simply overfitting on the validation data.

| ![ezgif com-gif-maker (4)](https://github.com/shankaattanayake/Data-Science/blob/main/Deep_Learning/ASL_Translator/Video/ezgif.com-gif-maker%20(2).gif) |

As can be seen in Figure: YOLOV5 Performance at 150 Epochs,  the Performance of the modelon the validation data had come out to be excellent. The model metrics of Precision, Recall andMean Average Precision at 0.5 and 0.5 to 0.95 had come out to over 80% in most classes.

| ![ezgif com-gif-maker (4)](https://github.com/shankaattanayake/Data-Science/blob/main/Deep_Learning/ASL_Translator/Video/ezgif.com-gif-maker%20(2).gif) |

## Model

| ![ezgif com-gif-maker (4)](https://github.com/shankaattanayake/Data-Science/blob/main/Deep_Learning/ASL_Translator/Video/ezgif.com-gif-maker%20(2).gif) |
