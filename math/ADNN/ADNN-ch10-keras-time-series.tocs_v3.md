![ADNN-ch10-keras-time-series](ADNN-ch10-keras-time-series.best.png)

- **10.1 Part 10.1: Time Series Data Encoding**
  - Time series encoding represents sequential events as input vectors with dimensions for sequences and features.
  - Feedforward neural networks always output the same result for given input, limiting time-series prediction.
  - Recurrent neural networks inherently handle temporal data without explicit encoding.
  - Examples show encoding stock prices and volumes as sequences suitable for time-series models.
  - Time series data is structured as sequences of fixed maximum length with input features per step.

- **10.2 Part 10.2: Programming LSTM with Keras and TensorFlow**
  - Recurrent neural networks use recurrent connections to maintain state and handle temporal dependencies.
  - Context neurons provide a mechanism to remember inputs from previous time steps without weighted input connections.
  - LSTM units contain forget, input, and output gates controlled by sigmoid and tanh activation functions.
  - Keras example builds an LSTM model for sequence classification using dummy variables and trains it effectively.
  - A sunspot prediction example uses LSTM regression with early stopping, demonstrating practical time-series forecasting.
  - Further reading: [Understanding LSTM Networks](https://colah.github.io/posts/2015-08-Understanding-LSTMs/).

- **10.3 Part 10.3: Text Generation with LSTM**
  - LSTM networks can generate free-form text character by character after training on large text corpora.
  - Text preprocessing includes lowercasing, character filtering, and converting characters to indexed vectors.
  - Training data consists of overlapping sequences with their next character as the target output.
  - The model uses softmax activation and temperature-based sampling to generate varied text outputs.
  - Example trained on *Treasure Island* demonstrates text generation improving across epochs.
  - Further reading: [The Unreasonable Effectiveness of Recurrent Neural Networks](https://karpathy.github.io/2015/05/21/rnn-effectiveness/).

- **10.4 Part 10.4: Image Captioning with Keras and TensorFlow**
  - Combines convolutional neural networks (InceptionV3 or MobileNet) with LSTM for generating image captions.
  - Dataset preprocessing includes cleaning captions, building vocabulary, and filtering low-frequency words.
  - Uses Glove embeddings for word representations integrated into the captioning model’s embedding layer.
  - Training uses a Keras data generator to efficiently produce batches pairing image features and caption sequences.
  - Caption generation is an iterative process predicting next words until a stop token or max length is reached.
  - Model performance evaluated on Flickr8k dataset and personal photos, showing good results on similar data.
  - Further reading: Andrej Karpathy’s Dissertation and related image captioning papers.

- **10.5 Part 10.5: Temporal CNN in Keras and TensorFlow**
  - Temporal CNNs use Conv1D layers to classify or regress sequential numeric data, as an alternative to LSTM.
  - Input sequences match LSTM format; Conv1D kernel size spans the entire sequence length.
  - Demonstrates simple sequence classification example with training and correct predictions.
  - Sunspot regression example applies stacked Conv1D layers with dropout and max pooling.
  - Model training uses early stopping to prevent overfitting and achieves reasonable RMSE performance.
  - CNNs provide a computationally efficient approach to time series modeling complementing LSTMs.
  - Further reading: research on CNNs applied to time series data.
