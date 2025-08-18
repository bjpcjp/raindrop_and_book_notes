[ADNN-ch10-keras-time-series](ADNN-ch10-keras-time-series.best.png)

- **10.1 Part 10.1: Time Series Data Encoding**
  - Time series encoding represents events over time for neural networks, necessary for feedforward networks since they output the same result for a given input.
  - Recurrent neural networks (RNNs) inherently handle temporal data without explicit encoding.
  - Input data for time series is structured with three axes: sequences, sequence members, and features.
  - Encoding examples show adding features (e.g., stock price and volume) and formatting sequences for LSTM input.
  - Time series encoding and RNNs provide alternative methods for forecasting based on temporal context.

- **10.2 Part 10.2: Programming LSTM with Keras and TensorFlow**
  - LSTM is a type of recurrent neural network unit that maintains internal state via gates: forget, input, and output gates.
  - Sigmoid and hyperbolic tangent (tanh) activation functions are central to LSTM gate operations.
  - Example code demonstrates building, training, and predicting with an LSTM model using Keras.
  - The sunspot prediction example illustrates LSTM regression on a large time-series dataset with early stopping.
  - Further reading includes resources on LSTM understanding and recurrent neural networks in TensorFlow.

- **10.3 Part 10.3: Text Generation with LSTM**
  - LSTMs can generate free-form text by learning sequences at the character or word level, producing stylistically similar but typically nonsensical output.
  - Text preprocessing includes cleaning, character indexing, and sequence vectorization to train the network.
  - A sample function uses temperature scaling with softmax for probabilistic character prediction.
  - Training runs with periodic sample generation to demonstrate progressive learning.
  - Relevant external resources include [The Unreasonable Effectiveness of Recurrent Neural Networks](http://karpathy.github.io/2015/05/21/rnn-effectiveness) and [Keras LSTM Generation Example](https://keras.io/examples/lstm_text_generation/).

- **10.4 Part 10.4: Image Captioning with Keras and TensorFlow**
  - Image captioning combines convolutional neural networks (CNNs) like InceptionV3 with LSTM text generation using transfer learning and GloVe embeddings.
  - The Flickr8k dataset is cleaned, tokenized, and prepared with start and stop tokens for captions.
  - Train/test splits and vocabulary pruning reduce noise by removing infrequent words.
  - A generator-based training process efficiently handles large datasets.
  - Caption generation iteratively predicts the next word until a stop token or max length is reached.
  - The captioning model performs well on Flickr8k images but less so on unrelated personal photos.
  - External resources: Andrej Karpathy’s dissertation on image captioning and the GloVe embedding project.

- **10.5 Part 10.5: Temporal CNN in Keras and TensorFlow**
  - Temporal CNNs apply 1D convolutional layers to sequence data, demonstrating efficacy on time-series classification tasks.
  - Data preparation closely mirrors LSTM sequence formatting, with conversion to dummy variables for categorical outputs.
  - Example network employs Conv1D layers followed by dense layers for classification.
  - A sunspot regression example uses sequential Conv1D, dropout, max pooling, and dense layers, trained with early stopping.
  - Model evaluation uses root mean squared error (RMSE) to quantify prediction accuracy.
