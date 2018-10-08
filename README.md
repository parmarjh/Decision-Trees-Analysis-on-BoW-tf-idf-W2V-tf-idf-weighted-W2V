# Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V #


## Amazon Fine Food Review Dataset ##

Data Source: https://www.kaggle.com/snap/amazon-fine-food-reviews

The Amazon Fine Food Reviews dataset consists of reviews of fine foods from Amazon. <br/>
Number of reviews                   : 568,454  <br/>
Number of users                     : 256,059  <br/>
Number of products                  : 74,258  <br/>
Timespan: Oct 1999                  : Oct 2012  <br/>
Number of Attributes/Columns in data: 10 <br/>

### Attribute Information ###
1. Id <br/>
2. ProductId - unique identifier for the product <br/>
3. UserId - unqiue identifier for the user <br/>
4. ProfileName <br/>
5. HelpfulnessNumerator - number of users who found the review helpful <br/>
6. HelpfulnessDenominator - number of users who indicated whether they found the review helpful or not <br/>
7. Score - rating between 1 and 5 <br/>
8. Time - timestamp for the review <br/>
9. Summary - brief summary of the review <br/>
10. Text - text of the review <br/>

## Objective ##

The code below would **clean the review text from html tags and punctuations and write it as a new column in the database and write it to disk**. This is further taken up in Part 2 to find accuracy of 10-fold cross validation KNN on vectorized input data, for each of the 4 featurizations, namely BoW, tf-IDF, W2V, tf-IDF weighted W2V.

## Significant Points ##

1. **Duplication of reviews** are found with same userid and timestamp (Cleaned).
2. Found discrepancy issues with HelpfulnessDenominator (Cleaned).
3. final.sqlite db is to be **used for further processing** such as Text to Vector operations.
4. The preprocessing step is one time effort but the training & visualization steps require multiple runs. Hence, it is prudent to make reprocessing step independant, to avoid multiple runs.

# Decision Trees on Amazon Reviews Dataset (Part II) #

## Data Source ##

The preprocessing step has produced final.sqlite file after doing the data preparation & cleaning. The review text is now devoid of punctuations, HTML markups and stop words.

## Objective ##

To find optimal depth using GridSearchCV or iterated cross validation (ideal for one hyperparameter) on standardized feature vectors obtained from BoW, tf-idf, W2V and tf-idf weighted W2V featurizations. <br/> <br/>
Find Precision, Recall, F1 Score, Confusion Matrix, Accuracy of 10-fold cross validation with GridSearch and Cross Validation with optimal Decision Tree model on vectorized input data, for BoW, tf-idf, W2V and tf-idf weighted W2V featurizations. TPR, TNR, FPR and FNR is calculated for all.

## At a glance ##

Tail end data is taken after sorting the data, to conserve the timing info & time Series based cross validation is done, as it is time series data. The optimal depth is found using GridSearchCV & Cross Validator, by searching for a range of depth 1-25.<br/><br/>
The Precision, Recall, F1 Score, Confusion Matrix, Accuracy metrics are found out for all 4 featurizations.

## Custom Defined Functions ##

2 user defined functions are written to<br/>
a) GridSearchCV for Optimal Depth Estimation<br/>
b) Compute DT Classifier Performance Metrics

## BoW ##

BoW will result in a sparse matrix with huge number of features as it creates a feature for each unique word in the review.<br/><br/>
For Binary BoW feature representation, CountVectorizer is declared as float, as the values can take non-integer values on further processing.

![1](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/1.PNG)

![2](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/2.PNG)

![3](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/3.PNG)

![4](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/4.PNG)

![5](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/5.PNG)

## tf-IDF ##

**Sparse matrix generated from tf-IDF** is fed in to GridSearch DT Cross Validator to find the optimal depth value.  <br/><br/>
Performance metrics of optimal DT with tf-idf featurization is found.

![6](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/6.PNG)

![7](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/7.PNG)

![8](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/8.PNG)

![9](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/9.PNG)

![10](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/10.PNG)

![11](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/11.PNG)

![12](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/12.PNG)

## Word2Vec ##

**Dense matrix generated from Word2Vec** is fed in to GridSearch DT Cross Validator to find the optimal depth value.  <br/><br/>
Performance metrics of optimal DT with W2V featurization is found.

![13](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/13.PNG)

![14](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/14.PNG)

![15](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/15.PNG)

![16](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/16.PNG)

![17](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/17.PNG)

![18](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/18.PNG)

## TF-IDWeighted W2V ##

![19](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/19.PNG)

![20](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/20.PNG)

![21](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/21.PNG)

![22](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/22.PNG)

## Summary Statistics ##

![23](https://github.com/AdroitAnandAI/Decision-Trees-Analysis-on-BoW-tf-idf-W2V-tf-idf-weighted-W2V/blob/master/images/23.PNG)

## Observations ##

1. The **GridSearchCV method and the 1-dimensional cross validation method with only depth as the hyperparameter, find out the same optimal depth** for the decision tree. <br/><br/>
2. It has also been noticed that **the cross validation error is high when d = 1 and then it would slowly decrease**. After the tree grows to some **optimal depth, around 5-15, depending on the data, the CV error would increase**. This property has been observed in all the 4 featurizations, as seen in the CV error vs d plots, above. The point where the CV error falls to the lowest point is identified to find optimal depth. <br/><br/>
3. Time-series based cross validation is used, as it is time series data. <br/><br/>
4. **As the number of points increase, the time taken for BoW and tf-idf increases rapidly. But, W2V featurization is found to be stable**, as dimension of W2V vector is a constant. <br/><br/>
5. The **best model** based on test metrics is found to be **DT on BoW**. But due to time constraints, **DT on W2V** may be more suitable when data is huge. BoW and tf-idf would create very high dimensional featurizations when the data is large. <br/>











