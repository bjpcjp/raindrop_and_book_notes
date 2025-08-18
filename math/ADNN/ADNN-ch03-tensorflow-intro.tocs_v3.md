[ADNN-ch03-tensorflow-intro](ADNN-ch03-tensorflow-intro.best.png)

- **3.1 Part 3.1: Deep Learning and Neural Network Introduction**
  - Neural networks were among the first machine learning models and are central to deep learning, especially with many hidden layers.
  - Inputs to neural networks vary in dimension, from 1D vectors to nD matrices, with CNNs accepting higher-dimensional inputs without flattening.
  - Neural networks perform classification and regression tasks, characterized by the number of output neurons and output type.
  - Neurons multiply inputs by weights, add a bias, then apply an activation function to produce outputs.
  - Neurons are organized into layers: input, hidden, output, bias, and context neurons, each with distinct roles.
  - Traditional activation functions include step, sigmoid, and hyperbolic tangent; modern networks use ReLU, softmax, and linear activations.
  - Bias neurons shift activation functions to enable better learning flexibility.
  - Context neurons maintain state in recurrent neural networks, important for time-series data.
  - For further reading, see [Deep Learning as the Third Generation of Neural Networks](https://www.soa.org/) (Society of Actuaries article).

- **3.2 Part 3.2: Introduction to TensorFlow and Keras**
  - TensorFlow is an open-source machine learning library developed by Google, widely used in research and production.
  - Key features include cross-platform support, GPU acceleration, and Python integration.
  - Keras offers a high-level API over TensorFlow, simplifying neural network creation and training.
  - Several competing deep learning tools exist, with PyTorch as the main alternative to TensorFlow/Keras.
  - TensorFlow provides low-level linear algebra operations and can be used beyond deep learning, e.g., Mandelbrot set rendering.
  - Neural network hyperparameters such as number of layers and neurons affect model performance; no universal best choice exists.
  - Keras training verbosity can be controlled using the verbose parameter in the fit method.
  - Regression and classification examples demonstrate hyperparameter tuning, data preprocessing, and evaluation metrics like RMSE and accuracy.
  - For further reading, visit the [TensorFlow Homepage](https://www.tensorflow.org/).

- **3.3 Part 3.3: Saving and Loading a Keras Neural Network**
  - Keras supports saving neural networks in three formats: YAML and JSON (structure only), and HDF5 (structure plus weights).
  - HDF5 is the recommended format for saving complete models, enabling future loading without retraining.
  - After training, models can be saved using model.save() and reloaded with load_model().
  - Reloaded models produce identical predictions and evaluation metrics as the original trained models.
  - For further documentation, see [Keras Model Saving](https://keras.io/guides/save_and_serialize/).

- **3.4 Part 3.4: Early Stopping in Keras to Prevent Overfitting**
  - Overfitting occurs when a model memorizes training data and fails to generalize, shown by divergence between training and validation error.
  - Datasets should be split into training, validation, and holdout sets for proper model evaluation.
  - Early stopping monitors validation loss during training and stops training once improvement stalls, restoring best weights.
  - EarlyStopping callback parameters include min_delta, patience, verbose, mode, and restore_best_weights.
  - Applying early stopping improves validation accuracy and prevents unnecessarily long training.
  - For further reading, see [Early Stopping in Keras](https://keras.io/api/callbacks/early_stopping/).

- **3.5 Part 3.5: Extracting Weights and Manual Network Calculation**
  - Weight initialization impacts training efficiency and performance; Xavier initialization uses normally distributed random weights centered at zero.
  - Xavier variance is computed as 2 divided by the sum of input and output neuron counts for the layer.
  - Neural networks can be inspected by extracting weights and biases per layer for manual calculations.
  - Training a simple XOR network demonstrates weight extraction and manual forward pass verification.
  - Manually computing neuron outputs with extracted weights and biases validates network training correctness.
  - For further reading, see [Understanding the difficulty of training deep feedforward neural networks (Glorot & Bengio, 2010)](http://proceedings.mlr.press/v9/glorot10a.html).
