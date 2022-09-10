# Contents

- [Contents](#contents)
- [Conclusion](#conclusion)
  - [models](#models)
    - [Convnets](#convnets)
  - [Fighting overfitting](#fighting-overfitting)
  - [Visualizing what convnets learn](#visualizing-what-convnets-learn)

# Conclusion

## models

### Convnets

Work by learning:
- a hierarchy of modular patterns
- concepts to represent the visual world

## Fighting overfitting

- regularization
  - L1/L2 regularization
  - dropout
- data augmentation
- use pretrained convnet
  - feature extraction from pretrained convnet with frozen converutional base 
  - fine-tuning pretrained convnet with a few top layers unfrozen in converutional base 

## Visualizing what convnets learn

- visualizing every channel in every intermediate activation
  - generate per layer activation and show as image
- visualizing convnet filters
  - defining the loss tensor for filter visualization
  - obtaining the gradient of the loss with regard to the input
  - normalizing the gradient
  - fetching numpy output values given numpy input values
  - maximizing loss via stochastic gradient decent
  - function to generate filter visualizations
  - generating a grid of all filter response patterns in a layer
- visualizing heatmaps of class activation
  - class-activation-map(CAM)
    - Grad-CAM
      - taking the output feature map of a convolution layer
      - given an input image
      - weighing every channel in the feature map by gradient of the class with respect to the channel