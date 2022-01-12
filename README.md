[![black](https://img.shields.io/badge/code%20style-black-000000.svg?style=plastic)](https://github.com/psf/black)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?color=g&style=plastic)](https://opensource.org/licenses/MIT)
[![Python 3.9](https://img.shields.io/badge/python-3.9-blue.svg)](https://www.python.org/downloads/release/python-390/)

# Fairness implications of encoding protected categorical attributes

Protected attributes are often presented as categorical features that need to be encoded before feeding them into a machine learning algorithm. Encoding these attributes is paramount as they determine the way the algorithm will learn from the data. Categorical feature encoding has a direct impact on the model performance and fairness. In this work, we compare the accuracy and fairness of the two most well-known encoders: One Hot Encoding and Target Encoding. We distinguish between two types of induced fairness that can arise while using these encodings. A first type is due to direct group category bias and a second type is due to large variance in minor groups. We take a deeper look into how regularization methods for target encoding can improve the induced bias while encoding categorical features. Furthermore, we tackle the problem of intersectional fairness that arises when mixing two protected categorical features leading to higher cardinality, boosting the model performance and increasing the discrimination of the machine learning model.

## Experiments



