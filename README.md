
# FairEncoder 


## Notes 22-Nov
Add vanilla experiemtn

Synthetic data
	One categorical features see the trade-off
	Easy examples

	One categorical feat + Non categorical

Objectives:
	1. Empirical study - Survey - 
	2. Role of regularization 
			tool to be used for fair models
			trade-off


Data:
	- Lawschool
## Notes 29 Nov
Target encodings are the industry standard for dealing with high cardinality categorical features. They do statistical aggregations of the target aiming to encode in a ordered categories. This statistical learning technique poses a risk towards bias preservation in machine learning models where categories encode some type of proteceted or discriminative information. 

It has been widely studied in the literature and applied in a plethora of machine learning tasks. However, the impact on fairness when encoding protected attributes
remains unknown. 

In this work we 

(𝑖) provide a survey of the different regularization methods of categorical variables,

 (𝑖𝑖) provide empirical evidence of the accuracy-fairness trade off when encoding categorical data

 (𝑖𝑖𝑖) analyze which encoding methods are
more suitable for bias mitigation procedures while maintaining the model performance.


#  Introduction

# Background -- Lit review
## Categorical Encodings (50%)
## Bias and fairness


# Methodology

## Regularization mehods
### M-estimator
### Exponential smoothing
### Gaussian Noise
### Leave one out??

## Dataset
### Compass
### 1 or 2 datasets
### Synthetical one (cauchy)
	Something else--
	Distribution where this is noticeable


## Models
### Linear
### GBDT
### NN

## Metrics ???

### Fairness metrics
	Equality of opportunity
	Difference of the true positive rate of the 2 groups

	Equalize odds
	Diference betwee false positive or the groups
	Diference betwee false negative or the groups

### Accuracy metrics
	AUC, Accuracy, Recall

# Experiments
For each regularizadion method
	for each dataset
		for each pair of metrics
			report results



Experiment 1
Using previous fairnes metrcis and a couple regularizers
check accuracy-fairenss tradeoff in compass



