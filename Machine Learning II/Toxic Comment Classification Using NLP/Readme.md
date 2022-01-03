**Toxic Comments Classification**

# **INTRODUCTION**

The internet and social media are one of the best innovations in the past century. However, there are a lot of problem they created at the same time. One of the significant issues is abuse of comments which leads to cyberbully and destroy the way we communicate. This project will use a publicly available dataset that contains toxic and non-toxic comments and try to identify them at the end after we train the models.

# **Problem statement**

We want to identify if a comment is toxic or not on social media to enable a better and healthier communication environment.

# **Data**
  ## Dataset
The dataset we chose for this project was found on Kaggle. It consist of comments from the Wikipedia’s talk page edits and it have already spited into 2 separate set: train and test. In both set, there are around 10% records are labeled as toxic. Both dataset each has over 150 thousand records and contains 9 features including: id, comment_text, id, toxic, severe_toxic, obscene, threat, insult, and identity_hate.  
  
Image

*Figure 1: Train vs Test Dataset*

Image

*Figure 2: Shape of Test Data*

Figure 3 shows for the distribution of tags in the train dataset. Note that the toxicity is not evenly spread out. Therefore, we must be careful about imbalance issues.

Image

*Figure 3: Distribution of tags in Train Data*

The Figure below shows how many comments have multiple tags. Some comments are tagged with more than one toxic tag.

Image

*Figure 4: Number of Comments with Multiple Tags*

The figure below shows the correlation of different tags.

Image

*Figure 5: Correlation of Different Tags*

## Data Cleaning

Image

*Figure 6: Raw Data Before Cleanup*

Image

*Figure 7: Data After Cleanup*

In Figure: Raw Data Before Cleanup, it can be seen what the raw data was before the cleanup process. In Figure: Data After Cleanup, it can be seen what the data looks like after the cleanup process. This was obtained by completing the following processes.


0. All the letters were converted to lowercase.

0. All newlines were removed.

0. Elements such as IP and username were removed.

0. Words with apostrophes were converted to two individual words. (Ex: “you’re” to “you are”)
0. Common words were taken out, such as “as”, “a”, “and”.

0. All non-alphanumeric and digit characters were removed.


