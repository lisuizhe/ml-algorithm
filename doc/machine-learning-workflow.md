# Contents

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