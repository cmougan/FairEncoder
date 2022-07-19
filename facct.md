SUBMISSION: 480
TITLE: Fairness implications of encoding protected categorical attributes

-------------------------  METAREVIEW  ------------------------
While the reviewers agreed that the topic being studied was well-suited for this conference, they felt that this paper isn't yet ready for publication.

The reviewers point out significant limitations in the paper, including
- Overly simplistic modeling choices (R1, R2)
- Unclear motivation (R1, R2)
- Lack of clear conclusions (R3)

I'd encourage the authors to integrate the reviewers' feedback in any future revisions.



----------------------- REVIEW 1 ---------------------
SUBMISSION: 480
TITLE: Fairness implications of encoding protected categorical attributes
AUTHORS: Carlos Mougan, Jose Alvarez, Gourab K Patro, Salvatore Ruggieri and Steffen Staab

----------- Overall evaluation -----------
SCORE: -2 (reject)
----- TEXT:
The authors examine different ways of encoding categorical sensitive/protected attributes for binary classification tasks. In particular,  they consider one-hot encoding (which encodes the k-th value of the sensitive attribute by the k-th standard basis vector) and several variants of target encoding (all of which encodes different values of the sensitive attribute by real numbers). Their goal is to study the effect of different encodings on the performance and group fairness of a binary classifier — where performance is measured by predictive accuracy or AUC and group fairness is measured by the difference in true positive rates across protected groups. 

If different encoding schemes have a non-negligible effect on the performance/fairness of binary classifiers, then an analysis of these effects could inform standard encoding schemes in ML.

My main concern with the paper is that the paper studies the setting where the dataset only has the labels and the sensitive attributes. That is, the dataset does not have any non-sensitive features. The authors justify this by saying that “It models situations in which [the sensitive attribute]  is the only observed attribute or all other observed attributes are not informative.“ I do not see any realistic setting where this would be true. Moreover, I do not see a way of extending the author's results beyond this setting. I encourage the authors to study the more realistic setting and see if their observations can be used to inform the ML practice.

My second concern is that even in the setting considered, many of the presented observations are imprecise and/or vague. I am giving two examples of such imprecision.

The authors differentiate the bias introduced by the encoding schemes into “irreducible” and “reducible” unfairness. In Section 2.2, they define these as “Irreducible bias refers to (direct) group discrimination arising from the categorization of groups into labels … Reducible bias arises due to the variance when encoding groups that have a small statistical representation, sometimes even only very few instances of the group.” These definitions seem vague to me even after I read the other discussion in the paper. This makes it hard to follow other observations and claims that are stated in terms of irreducible and reducible biases. I think adding precise definitions of these terms – using the notation in Section 3 –would be very useful for the paper.

In lines 417 to 428, the authors argue that target encoding with Gaussian noise can correct irreducible unfairness under some settings. This analysis is hard to follow and seems to be imprecise. For example, line 417 says “assume that \hat{p}_i is concentrated over p_i with probability 1, namely, we have perfect target encoding with Gaussian noise.” Here, “concentrated over p_i with probability 1” is unclear — perhaps the authors mean that \hat{p}_i is equal to p_i for the given draw of the dataset? Next, line 423 says “…to estimate P(Y= +| X = x_i) closer to the observed proportion of the majority categories.” Here, “observed proportion of the majority categories” is unclear — perhaps the authors meant the observed proportion of positive labels in the reference category?


Minor suggestions
1. I think it would be useful to define some of the terms used in the paper (e.g., AUC, prediction/classification error)  at the beginning of Section 3.
2. Some suggestions for improving the figures: Table 1 overflows the horizontal margin and the statistics of smaller groups are not readable in Figure 1.
----------- Ethical review -----------
This paper does not require an ethical review.



----------------------- REVIEW 2 ---------------------
SUBMISSION: 480
TITLE: Fairness implications of encoding protected categorical attributes
AUTHORS: Carlos Mougan, Jose Alvarez, Gourab K Patro, Salvatore Ruggieri and Steffen Staab

----------- Overall evaluation -----------
SCORE: -2 (reject)
----- TEXT:
Summary of contributions: This paper studies the relationship between the encoding of a categorical protected attribute in a binary classification model and the resulting difference in true positive rates across groups, or equality of opportunity measures. Specifically, they compare simple one-hot encoding with "target smoothing," where "categorical features are replaced with the mean target value of each respective category." Theoretically, they study simple examples when the binary classifier makes decisions solely based on the protected attribute, and look at the effects of target smoothing on differences in true positive rates. Empirically, they train logistic regression models and and decision trees with target smoothing on two benchmark datasets.

----------
Strengths:
- The differentiation between "irreducible" and "reducible" bias is helpful. The most significant contribution of this work in my opinion is the split characterization of irreducible and reducible bias under different smoothing/regularization methods.

- The techniques of target smoothing and Gaussian regularization are mostly clearly presented and simple to implement.

----------
Weaknesses:

- This paper is missing any discussion on the relationship between the categorical feature encoding and the architecture of the model taking that encoding as input. This is a significant gap in practical relevance.

- In their theoretical section, they look at a very simple example where the binary classifier \hat{Y} depends solely on the protected attribute, and the goal is to maximize accuracy. It's not clear how their analysis would extend to different model function classes or different objective functions, possibly with fairness constraints built into the optimization problem. Perhaps they could extend their theoretical study to look at different modeling assumptions, such as the linear models or decision tree models they apply in experiments.

- This paper specifically looks at how changing a categorical feature encoding solely affects resulting true and false positive rates for subgroups. The practical utility for this is not clear to me -- do they expect practitioners to change the encoding of their features as an intervention to satisfy the equality of opportunity measure? In that case, why not compare to other interventions for satisfying equality of opportunity? As it stands, it's unlikely that a practitioner concerned about fairness would rely solely on changing a categorical feature encoding to achieve fairness goals when they have access to so many other ways of achieving equality of opportunity. This paper also does not provide enough experimental or theoretical evidence to encourage a practitioner to do so. To improve in practical relevance with respect to recent fairness literature, I might suggest that the authors explore how different methods for enforcing fairness change when the categorical feature e
ncoding changes.

- The paper only looks at a single fairness metric of equal opportunity.

- In the experiments section 5.4 on Reducible bias, they sample a 0.002 fraction of the African-American subset of data and compare this with the full sample. Unfortunately, they only draw one such sample. Thus, any results would be dependent on this sample, and it would be hard to draw any statistically significant conclusions. For such a tiny fraction, I would suggest resampling the 0.002 subsample multiple times and reporting a mean and standard error of the resulting fairness and AUC measures in Figure 4.

The notation is unclear in several places:
- They refer to a scoring function \hat{S} several times in Section 4, but this scoring function is not properly introduced or defined. Is \hat{S} estimating some true scoring function S?

- The theoretical discussion of the effects of Gaussian noise in lines 418-423 is confusing to me. Line 409 suggests that they add Gaussian noise directly to the target encoding estimator \hat{p}_i. How does this lead to a change in the observed proportion of positives for X = x_i, or a change in the instances in the training set (lines 418-419)? Are they resampling the x_i after adding Gaussian noise? 

----------
Overall evaluation: This paper's contributions seem too sparse in my opinion. The theory is not really relevant enough to practice. The overall idea of using smoothing to enforce fairness is also highly dependent on the model architecture, which this paper does not address.



----------------------- REVIEW 3 ---------------------
SUBMISSION: 480
TITLE: Fairness implications of encoding protected categorical attributes
AUTHORS: Carlos Mougan, Jose Alvarez, Gourab K Patro, Salvatore Ruggieri and Steffen Staab

----------- Overall evaluation -----------
SCORE: 0 (borderline paper)
----- TEXT:
This paper considers implications of how one encodes sensitive categorical attributes. In order to run a machine learning algorithm one needs to convert categorical random variables into mathematical forms. One-hot encoding and target encoding are two of the most natural and popular methods to solve this problem. This paper studies the implications of both these encodings on fairness. Naturally when the number of examples with a particular value of the protected attribute are low, the models tend to "overfit" and cause high variance. The paper proposes smoothing such as +1/Gaussian smoothing.

The positives:
- Studies a problem with strong practical and societal relevance. As machine learning gets even more prevalent, simple issues such as how categorical random variables are selected can have major impact down the line.

Negatives:
- the experiments and their explanations are not well written.
- the theoretical components and ideas are straightforward which is generally a good thing. Here there are no strong conclusions drawn from it so I do not see a compelling evidence drawn from the proposed theoretical analysis.

Overall the paper looks at a really relevant problem but gives lukewarm results. If it is accepted, it should be based on the former.