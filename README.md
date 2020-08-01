# AdaptiveLRF
This is the implementation of AdaptiveLRF [1]. This code was written based on `keras/tensorflow` and tested on `tensorflow 1.15.0`.

## How to use?
The code contains just a class named `AdaptiveLRF`. This class extends `Callback` (a class in `keras` library). 
Then, what just you need to do is add a instance of this class in your callback list in `fit` function.

## Create an instance
The constructor parameter is in the following:
1. A trainable model. The acceptable type is `keras.models.Model`.
2. The number of the classes. The acceptable type is `int`.
3. A part of the input of the train samples. The acceptable type is `numpy.ndarray`.
4. A part of the output of the train samples. The acceptable type is `numpy.ndarray`.
7. The batch size which the conditional analysis is done on this size of the batch. The acceptable type is `int`.
8. The value of `k`. This value was described in the paper.
9. The number of patients after overfitting.

## An small example
```
model.compile(...)
reg = AdaptiveLRF(model, 10, ...)
model.fit(..., callbacks=[reg])
```

Notice, you have to give the validation or test data to the `fit` function!

## Reference
[1] Mohammad Mahdi Bejani and Mehdi Ghatee, Adaptive Low-Randk Factorization to Regularize Shallow and Deep Neural Networks, ArXiv, 2020
