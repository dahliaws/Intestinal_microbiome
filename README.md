# Intestinal_microbiome

Analyzing the distinction between the microbiome healthy vs IBD individuals.

Inflammatory Bowel Disease - A term which describes 2 conditions:

- Crohn's Disease
- Ulcerative colitis

Both conditions are autoimmune diseases of the gastrointestinal (GI) tract.
The exact cause is unknown. It is believed to be the result of a weakened immune system.


This project does not include enough data for ML algorithms. 
However, it is an analysis of the bacterial profile of sick vs a healthy individuals. 

2 datasets are analyzed in this project:
1. Df_users_IBD - Clinical data on the individuals in the study
2. Mpa_data_IBD - Relative abundance →(Percent composition of an organism of a particular kind relative to the total number of organisms in the area.) of the different organisms found in the stool samples of each individual in the study.

### EDA of mpa_data:
The initial shape: (750, 1514)
Each column was the name microorganism with their taxonomic rank.
The two columns from df_users were merged with mpa_data on patient_ID and was renamed mpa_new. 
As expected, the vast majority of flora in the gut was bacteria.

### Data mining of map_new DataFrame:
1. Removed columns with missing values. (750 rows, 1167 columns)
2. Retained only bacterial kingdom. (750 rows, 1062 bacterial columns)
3. Divide the table to two tables - IBD (181, 1062) and healthy (569, 1062)
   Compare the differences of "what is" in the GI of a healthy person vs. a sick person.
 
New DataFrames (b1 and b0) retained all non-zero relative abundance scores.
	b1 = 181 rows with IBD, 11 bacterial columns 
	b0 = 569 rows with healthy individuals, 15 bacterial columns

Some of the bacteria was not labeled past the class or phylum. This made it difficult to know if they were, in fact different bacteria to those labeled down to the genus or species.


### Conclusions:

Patients with IBD have a different microbiome profile than healthy individuals.

Their intestinal microflora is less diverse.
The remaining bacteria found in the GI of IBD individuals is imbalanced in contrast to the profile of a healthy GI. 

With more data a supervised learning algorithm could be used to classify the target, IBD.
 
1. Random Forest would work well with this dataset. <br>
	a. Enhance data by bootstrapping so that we are not using the same data for every tree (less sensitive to training data like DT).<br>
	b. Less features will be used to train each tree.<br>
		i. Some trees will have less-important  features leading to bad prediction but other trees will give bad predictions in the opposite direction (hence it balances out).<br>
	c. Majority voting or Aggregation - combining results from multiple models.<br>
2. Metrics -confusion matrix and a classification report can provide: <br>
	a. Accuracy <br>
	b. Recall - tells us how many true positives were retrieved. <br>
	c. Precision -number of correctly-identified members of a class divided by all the times the model predicted that class.<br>

3. validate model performance <br>
	a. K-fold cross validation<br>
		i. splitting the training dataset into k folds.<br>
	b. holdout kth fold is used as the test set.<br>


 
