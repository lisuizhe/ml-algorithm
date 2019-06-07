# Contents
- [Input Modalities and Appropriate Network Architectures](#Input-Modalities-and-Appropriate-Network-Architectures)
- [Dense](#Dense)
- [Convnets](#Convnets)
- [Rnns](#RNNs)

# Input Modalities and Appropriate Network Architectures

- Vector data: Dense
- Image data: Conv2D
- Sound data: Conv1D(preferred) or RNNs
- Text data: Conv1D(preferred) or RNNs
- Timeseries data: RNNs(preferred) or Conv1D
- Other type of sequence data: RNNs if data ordering is strongly meaningful or Conv1D otherwise
- Video data: Conv3D or Conv2d(for feature extraction) followed by RNN or Conv1D(for processing result sequences)
- Volumetric data: Conv3D

# Dense

## Binary Classfication

End the stack of layers with a **Dense** layer with a **single** unit and a **sigmoid** activation, use **binary_crossentropy** as the loss

```python
model = models.Sequential()
model.add(layers.Dense(32, activation='relu', input_shape=(num_input_features,)))
models.add(layers.Dense(32, activation='relu))
model.add(layers.Dense(1, activation='sigmoid))
model.compile(optimizer='rmsprop', loss='binary_crossentropy')
```

## Single Label Categorical Classfication

End the stack of layers with a **Dense** layer with a number of units **equal to the number of classes**, and a **softmax** activation, use **categorical_crossentropy**(if targets are one-hot encoded) or **sparse_categorical_crossentropy**(if targets are integers) as the loss

```python
model = models.Sequential()
model.add(layers.Dense(32, activation='relu', input_shape=(num_input_features,)))
models.add(layers.Dense(32, activation='relu))
model.add(layers.Dense(num_classes, activation='softmax))
model.compile(optimizer='rmsprop', loss='categorical_crossentropy')
```

## Multilabel Categorical Classfication

End the stack of layers with a **Dense** layer with a number of units **equal to the number of classes**, and a **sigmoid** activation, use **binary_crossentropy**(targets should be one-hot encoded) as the loss

```python
model = models.Sequential()
model.add(layers.Dense(32, activation='relu', input_shape=(num_input_features,)))
models.add(layers.Dense(32, activation='relu))
model.add(layers.Dense(num_classes, activation='sigmoid))
model.compile(optimizer='rmsprop', loss='binary_crossentropy')
```

## Regression

End the stack of layers with a **Dense** layer with a number of units **equal to the number of values**, and **no** activation, use **mae** or **mse** as the loss

```python
model = models.Sequential()
model.add(layers.Dense(32, activation='relu', input_shape=(num_input_features,)))
models.add(layers.Dense(32, activation='relu))
model.add(layers.Dense(num_values))
model.compile(optimizer='rmsprop', loss='mse')
```

# Convnets

Consist of stacks of **convolution** and **max-pooling** layers(to extract spatial features). Often ended with either a **Flattern** operation or a **global pooling** layer(to turn spatial feature maps into vectors), followed by **Dense** layers to achieve classfication or regression.

Tradition convolution may be replced by **depthwise separable convolution** or **octave convolution**.

```python
model = models.Sequential()
model.add(layers.SeparableConv2D(32, 3, activation='relu', input_shape=(height, weight, channels)))
model.add(layers.SeparableConv2D(64, 3, activation='relu'))
model.add(layers.MaxPooling2D(2))

model.add(layers.SeparableConv2D(64, 3, activation='relu'))
model.add(layers.SeparableConv2D(128, 3, activation='relu'))
model.add(layers.MaxPooling2D(2))

model.add(layers.SeparableConv2D(64, 3, activation='relu'))
model.add(layers.SeparableConv2D(128, 3, activation='relu'))
model.add(layers.GlobalAveragePooling2D())

model.add(layers.Dense(32, activation='relu'))
model.add(layers.Dense(num_classes, activation='softmax'))

model.compile(optimizer='rmsprop', loss='categorical_crossentropy)
```

# RNNs

Prior to the last layer, RNNs should return full sequence of its outputs. For last layer of RNNs, return only last output which contains information about the entire sequence.

Use **LSTM** or **GNU**. May be replaced by **Transformer** on sequences data.

```python
model = models.Sequential()
model.add(layers.LSTM(32, return_sequences=True, input_shape=(num_timesteps, num_feature)))
model.add(layers.LSTM(32, return_sequences=True))
model.add(layers.LSTM(32))
model.add(layers.Dense(num_classes, activation='sigmoid'))
model.compile(optimizer='rmsprop', loss='binary_crossentropy')
```