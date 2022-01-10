# Natural Language Processing Techniques 
## Introduction:
In this Project, the following Natural Language Processing methods were experimented with. 

•	Bag of Words
•	TF-IDF
•	Character N Gram
•	Word N Gram

Natural Language Processing bridges the gap between how humans communicate and how computers communicate. For Machine Learning Algorithms to use languages used by humans, Natural Language Processing methods convert the Human Languages to Numerical Values. Numerical values are the only form of values accepted by most simple Machine Learning Algorithms. 

## Bag of Words:

Steps for Bag of Words is as follows:
1.	Tokenize the sentences into words
2.	Create Dictionary of Word Frequency
3.	Bag of Words Model

Image

Figure 1: Bag of Words Models of "I like to play football", "Did you go outside to play tennis", and "John and I play tennis”

The Bag of Words Model with their respective Labels can be used to train a Machine Learning Algorithm.

## TF-IDF:

TF-IDF is used to give words that appear less frequently more gravity than others using the steps below.
1.	Tokenize the sentences into words
2.	Create a Dictionary of word frequency
3.	Sort the dictionary with word frequency
4.	Compute Term frequency
5.	Compute Inverse Document frequency
6.	Compute TF-IDF values

Image

Figure 2: Term Frequency

Image 

Figure 3: Inverse Term Frequency

Image

Figure 4: TF-IDF Value
The TF-IDF Values of each sentence can be sent to Machine Learning Algorithms to train the model.

## Character & Word N Gram

Character and Word N Gram can be used to help with retaining the context in a sentence without treating each word separately, unlike the methods demonstrated above. 
Steps to take for Character & Word N Gram are as follows:
1.	Import all the necessary libraries
2.	Extract the contents of article of interest
3.	Clean the extracted text
4.	Build the N-Grams model
5.	 Generate sequence
 
 Image
 
Figure 5: Character N-Gram
 
 Image
 
Figure 6: Word N-Gram

## Conclusion:

There are many methods of Natural Language Processing. Each with their benefits and disadvantages. All different methods were experimented and can be viewed in the Jupyter Notebooks in the same folder as this Readme file.

