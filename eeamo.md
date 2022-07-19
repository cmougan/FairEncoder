SUBMISSION: 52
TITLE: Fairness implications of encoding protected categorical aributes

-------------------------  METAREVIEW  ------------------------
The reviewers agree that the paper is relevant to EAAMO and that data preprocessing is an important topic. However, there are concerns about the specific evaluations/experiments performed, and broader ethical concerns about whether target encoding is ever appropriate for sensitive attributes. I’d also like to add that the paper may benefit from a more detailed discussion of how the results interact with choices for whether to include the sensitive attribute at all.



----------------------- REVIEW 1 ---------------------
SUBMISSION: 52
TITLE: Fairness implications of encoding protected categorical aributes
AUTHORS: Carlos Mougan, Jose Alvarez, Gourab Patro, Salvatore Ruggieri and Steffen Staab

----------- Summary -----------
This paper examines the effects of encoding protected categorical attributes on the fairness and accuracy of machine learning models. It provides a comparative evaluation of two encoding methods: dummy variables (common in the social sciences) and target encoding. Considering interactions between primitive attributes (like race and gender) increased the cardinality of the set of complex or intersectional attributes, making dummy variables less appealing. But target encoding, which is based on the expected value of a binary target variable conditional on membership of a category, imposes an artificial ordinal structure on the data. The paper uses two real world data sets (COMPAS and LSAC) to examine implications of encoding choices for bias, evaluated based on differences in the true positive rate for the protected category relative to a reference group. The main finding is that the dummy variable approach results in more bias than target encoding.
----------- Strengths -----------
The topic of algorithmic bias is relevant for EAAMO, and the problem of dimensionality arising from interactions of attributes is important.
----------- Weaknesses -----------
See comments below on measure of bias and target encoding.
----------- Overall evaluation -----------
SCORE: 0 (borderline paper)
----- TEXT:
I don't find the measure of bias based on the TPR to be convincing. For example, if there are no true positives for recidivism in the COMPAS data, so all recidivists are false negatives, the measure will indicate bias against the protected category. This is a measure of inaccuracy rather than bias. There are better measures of bias based on outcomes in the social science literature.

In addition, the fact that target encoding imposes an artificial order on the data is troubling. There are better approaches to dealing with prediction biases based on protected attributes, for example to two-step procedure discussed here:

Yang, Crystal S., and Will Dobbie. “Equal protection under algorithms: A new statistical and legal framework.” Michigan Law Review 119, no. 2 (2020): 291-395.



----------------------- REVIEW 2 ---------------------
SUBMISSION: 52
TITLE: Fairness implications of encoding protected categorical aributes
AUTHORS: Carlos Mougan, Jose Alvarez, Gourab Patro, Salvatore Ruggieri and Steffen Staab

----------- Summary -----------
This paper assesses performance and fairness implications of two different approaches to encoding protected categorical features (one hot encoding and target encoding). The authors hereby distinguish two types of bias: irreducible and reducible bias. The paper involves both theoretical and empirical parts.
----------- Strengths -----------
The paper is neatly written and easy to read. The topic is clearly relevant to the EAAMO community. Examining effects of different encoding approaches is under-researched and needed. I believe that this paper can trigger interesting discussions and can be of value to researchers and practitioners from different disciplines.
----------- Weaknesses -----------
- One of my major concerns about the analysis is that I do not understand whether and why it would be meaningful to perform target encoding on categorical data such as gender, ethnicity, etc. Why would it be desirable to impose an ordering of features that can and should not be ordered? E.g., Tab. 1 looks highly problematic to me. The authors should make this clearer.
- The authors should make it clearer how in Tab. 1 “Hispanic” is assigned the target encoding 0 and “African-American” is assigned 1. The cases seem symmetric in the one hot encoding case. What is meant by “target” here?
- The abstract contains no information re. the authors’ findings (neither theoretical nor empirical). I would have liked to see key findings highlighted early on in the paper, starting with the abstract.
- The implications from the theoretical section seem somewhat unclear to me. I’d suggest the authors make this clearer and provide the reader with clear “takeaways”. Right now, the theoretical section feels a bit like a “foreign body” without much of discussion and interpretation. Among others, some intro to section 4 would have been helpful.
- In the experimental section (sec. 5), it seems a bit limiting to only consider equal opportunity fairness. How are the effects on the myriad of other fairness concepts? Would the results -- e.g., that one hot encoding leads to more discriminatory results -- generalize?
- It would be interesting to also compare other ways of encoding features.
----------- Overall evaluation -----------
SCORE: -1 (weak reject)
----- TEXT:
I recommend weak reject based on my review above.
----------- Ethical considerations -----------
I think this type of work is important, but I am unclear as to whether a target encoding (imposing an ordering) would ever be a good idea when it comes to sensitive features such as gender or ethnicity.



----------------------- REVIEW 3 ---------------------
SUBMISSION: 52
TITLE: Fairness implications of encoding protected categorical aributes
AUTHORS: Carlos Mougan, Jose Alvarez, Gourab Patro, Salvatore Ruggieri and Steffen Staab

----------- Summary -----------
The paper studies how two categorical feature encoding techniques — one-hot encoding and target encoding — might affect the fairness of a machine learning model. With an emphasis on target encoding, the authors of the paper decompose the bias induced from this encoding into “irreducible bias”, which is due to the inherent discrimination of the model, and “reducible bias” which is due to the large variance on small sample sizes. This paper is relevant to the EAAMO conference because it discusses issues of fairness as it relates to data preprocessing in machine learning.
----------- Strengths -----------
a) Background and Intro sections are explained rather clearly
b) Directly related to topics of fairness theory and ML
c) Novel and interesting pre-processing step exploration to promote fairness in ML models. Theory seems to also be novel.
d) Encoding is a very common step in data processing, so this work relates to a variety of fields tangential to ML
----------- Weaknesses -----------
a) Unfortunately, there are many methodological problems in their experiments, which raises questions as to the usefulness of their novel method. The authors also lacked depth and clarity in explaining the methods and results.
b) The narrow and theoretical scope of the paper does not lend itself to be particularly interesting for policymakers or practitioners.
c) (Criticisms are mostly about the impact of their novel contributions) Very specific comparison of two encoding methods, one of which (target encoding) is not a very popular method.
d) Their conclusion that one-hot encoding is often more biased than target encoding is specific only to the one dataset they used, to the one experiment (split) they ran, and to one fairness metric. Even if it is true in general, other works can easily bypass this problem by employing very effective existing methods to promote fairness (in-processing or post-processing ML approaches). In short, the findings do not invite much interdisciplinary follow-up work.
----------- Overall evaluation -----------
SCORE: -2 (reject)
----- TEXT:
Apart from the strengths and weaknesses outlined above, my main objections about this paper is their methodology and results, which includes the following list:
⁃ Why only use equal opportunity? Is there a justification?
⁃ Reducible bias experiments: only uses one split despite sampling such a low sample (0.02%) of the Black population. I would expect multiple splits, then averaging the results to get a better idea of performance
⁃ No discussion on why the regularization does not help in the irreducible noise experiments — authors say the hyperparameter is “over-tuned”, but how can you over-tune a hyperparameter? Was there even tuning involved, since it doesn’t seem like there is a validation set used to tune
⁃ Figure 4 indicates that the y-axis (eq opp fairness) does not compare Black vs White defendants, but Black vs. a sample of the Black population. What is the intuition of this metric? It makes the interpretation of the graph unclear and no explanation is given.
- Figure 4 continued: why only show logistic regression? What about the other models stated in the methods section?
⁃ Paper also claims to use Law School Admissions data, but all results only involve the COMPAS dataset
----------- Ethical considerations -----------
While this paper centers around making algorithms more fair, there is unfortunately a dearth of discussion in the ethical considerations of their method. For instance, the authors choose to use Equal Opportunity  to assess model fairness, but offer no explanation as to why it is appropriate for the experiment’s context. The authors also argue that using a regularized target encoding method often leads to fairer models, but that is not consistently seen in their results — by the end of the paper, the ethical implications of using various encoding methods remains unclear and convoluted.