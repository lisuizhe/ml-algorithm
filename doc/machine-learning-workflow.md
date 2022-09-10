# Contents

- [Contents](#contents)
- [Defining the problem and assembling a dataset](#defining-the-problem-and-assembling-a-dataset)
- [Choosing a measure of success](#choosing-a-measure-of-success)
- [Deciding on an evaluation protocol](#deciding-on-an-evaluation-protocol)
- [Preparing data](#preparing-data)
- [Developing a model that does better than a baseline](#developing-a-model-that-does-better-than-a-baseline)
  - [If cannot beat random baseline](#if-cannot-beat-random-baseline)
  - [If goes well](#if-goes-well)
- [Scaling up: developing a model that overfits](#scaling-up-developing-a-model-that-overfits)
- [Regularizing model and tuning hyperparameters](#regularizing-model-and-tuning-hyperparameters)
- [Advanced skills](#advanced-skills)
- [Debuging a learning algorithm](#debuging-a-learning-algorithm)
  - [check bias and variance](#check-bias-and-variance)
  - [fix high bias](#fix-high-bias)
  - [fix high variance](#fix-high-variance)
  - [error analysis](#error-analysis)
- [Getting more data](#getting-more-data)

# Defining the problem and assembling a dataset

1. input/output data
2. type of problem:
  - binary classification
  - multiclass classification
  - scalar regression
  - vector regression
  - multiclass, multilabel classfication
  - clustering
  - generation
  - reinforcement learning
3. unsolvable problems:
  - nonstationary problems

# Choosing a measure of success

1. balanced-classfication:
  - accuracy
  - area under the receiver operating characteristic curve
2. class-imbalanced classfication:
  - precision
  - recall
3. ranking:
  - mean average precision
4. multilabel classification:
  - mean average precision
5. others:
  - custom metircs
  - check kaggle about problems and their evaluation metrics

# Deciding on an evaluation protocol

1. hold-out validation
2. k-fold cross-validation
3. iterated k-fold validation

# Preparing data

1. vectorization
2. normalization
  - range to [-1, 1] or [0, 1]
  - mean and average
3. missing feature
4. feature engineering

# Developing a model that does better than a baseline

## If cannot beat random baseline

- the hypethesize may be false:
  - outputs can be predicted given inputs
  - avaiable data is sufficiently informative to learn the relationship between inputs and outputs

## If goes well

- key choices to model
  - last-layer activation
  - loss function
  - optimization configuration
    - optimizaer
    - learning rate

| Problem type | Lasy-layer activation | Loss function |
| ------------ | --------------------- | ------------- |
| Binary classification | sigmoid | binary_crossentropy |
| Multiclass, single-label classification | softmax | categorical_crossentropy |
| Multiclass, multiabel classification | sigmoid | binary_crossentropy |
| Regression to arbitrary | None | mse |
| Regression to values between 0 and 1 | sigmoid | mse or binary_crossentropy |

# Scaling up: developing a model that overfits

1. add layers
2. make the layers bigger
3. train for more epochs
4. monitor the training and validation loss as well as metrics you care

# Regularizing model and tuning hyperparameters

1. add dropout
2. try different architectures: add or remove layers
3. add L1 and/or L2 regularization
4. try different hyperparameters to find optimal configuration
  - number of units per layer
  - learning rate
5. feature engineering
  - add new features
  - remove features that do not seem to be informative

# Advanced skills

1. batch normalization
2. depthwise separable convolution
3. residual connection
4. model ensembling
  - tree-based method(random forest or gradient-boosted trees)
  - dnn
5. (automated) hyperparameter optimization
6. transfer learning
  - supervised pretraining
  - fine tuning
    - option1: only train output layers parameters
    - option2: train all parameters

# Debuging a learning algorithm

## check bias and variance

- bias = loss_train - loss_baseline
- variance = loss_validation - loss_train

## fix high bias

- try getting additional features
- try adding polynomial features
- try decreasing lambda(regulation parameter)

## fix high variance

- get more training examples
- try smaller sets of features
- try increasing lambda(regulation parameter)

## error analysis

- manually find 100 errors and group them
- focus on major error group
  - add more data on error group
  - add feature for error group

# Getting more data

- data augmentation
- data synthesis
