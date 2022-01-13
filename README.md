# Linkage  

Data linkage will be performed on two  datasets and explore different classification algorithms.  
  
The project is to be coded in Python 3. Seven (7) relevant data sets can be downloaded:
  
• datasets for Data Linkage  
– amazon.csv  
– google.csv  
– amazon google truth.csv  
– amazon small.csv  
– google small.csv  
– amazon google truth small.csv  
• dataset for Classification: all yeast.csv  
  
**Part 1 - Data Linkage** 
  
*Na¨ıve data linkage without blocking*  
Using amazon small.csv and google small.csv, implement the linkage between the two data sets and measure its performance. Comment on your choice of similarity functions, method of deriving a final score, and the threshold for determining if a pair is a match.  
The performance is evaluated in terms of recall and precision. Ground truth (true matches) are given in amazon google truth small.csv.  
recall = tp/(tp + fn)  
precision = tp/(tp + f p)  
where tp (true-positive) is the number of true positive pairs, f p the number of false positive pairs, tn the number of true negatives, and fn the number of false negative pairs. The four numbers should sum up to the total number of all possible pairs from the two datasets. (n = f p + fn + tp + tn)  
  
*Blocking for efficient data linkage*   
Implement a blocking method for the linkage of the amazon.csv and google.csv data sets and report on your proposed method and the quality of the results of the blocking.  
To measure the quality of blocking, we assume that when comparing a pair of records, we can always determine if the pair are a match with 100% accuracy. With this assumption:  
• a record-pair is a true positive if the pair is found in the ground truth set and also the pair are in the same block.  
• a record-pair is a false positive if the pair co-occur in some block but are not found in the ground truth set.  
• a record-pair is a false negative if the pair do not co-occur not in any block but are found in the ground truth set.  
• a record-pair is a true negative if the pair do not co-occur not in any block and are also not found in the ground truth set.  
Then, the quality of blocking can be evaluated using the following two measures:  
Pair completeness (P C) = tp/(tp + fn)  
Reduction ratio (RR) = 1 − (tp + fp)/n  
where n is the total number of all possible record pairs from the two data sets. (n = f p + fn + tp + tn)    
  
**Part 2 - Classification**  
  
*Pre-processing*    
• Impute missing values: Use replacement by mean and replacement by median to fill in missing values. Display the min, median, max, mean and standard deviation for the data with imputations. Justify which imputation method is more suitable.  
• Scale the features: Explore the use of two transformation techniques (mean centering and standardisation) to scale all attributes after median imputation, and compare their effects. Display the min, median, max, mean and standard deviation for the both types of data scaling.  
  
*Comparing Classification Algorithms*  
compare the performance of the following 3 classification algorithms: k-NN (k=5 and k=10) and Decision tree algorithms on the all yeast dataset.  
Use the data, all yeast, as transformed in the pre-processing (mean centered, median imputed). Train the classifiers using 2/3 of the data and test the classifiers by applying them to the remaining 1/3 of the data. Use each classification algorithm to predict the Class feature of the data (CYT or non-CYT) using the first 8 features (mcg-nuc).  

*Feature Engineering*  
In order to achieve higher prediction accuracy for k-NN, one can investigate the use of feature generation and selection to predict the Class feature of the data. Feature generation involves the creation of additional features. Two methods are:  
• Interaction term pairs. Given a pair of features f1 and f2, create a new feature f12 = f1 × f2 or by f12 = f1 ÷ f2. All possible pairs can be considered.  
• Clustering labels: apply k-means clustering to the data in all yeast data and then use the resulting cluster labels as the values for a new feature fclusterlabel. At test time, a label for a testing instance can be created by assigning it to its nearest cluster.  
Given a set of N features (the original features plus generated features), feature selection involves selecting a smaller set of n features (n < N). Here one computes the mutual information between each feature and the class label (on the training data), sorts the features from highest to lowest mutual information value, and then retains the top n features from this ranking, to use for classification with k-NN.  
In the last, we will evaluate whether the above methods for feature generation and selection, can deliver a boost in prediction accuracy compared to using k-NN just on the original features in all yeast.  
