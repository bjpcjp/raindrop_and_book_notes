[ADNN-ch11-nlp-spacy](ADNN-ch11-nlp-spacy.best.png)

- **11.1 Part 11.1: Getting Started with Spacy in Python**
  - The section explains the choice between character-level and word-level NLP methods using neural networks.
  - It introduces two prevalent NLP libraries for Python: NLTK and Spacy, with a focus on Spacy for its object abstraction capabilities.
  - Instructions for installing Spacy and necessary language models are provided, including the command `python -m spacy download en`.
  - Demonstrates tokenization, part-of-speech tagging, entity recognition, sentence diagramming, lemmatization, and handling of stop words using Spacy.
  - Further reading: [Spacy Official Documentation](https://spacy.io/usage)

- **11.2 Part 11.2: Word2Vec and Text Classification**
  - Word2Vec models create numeric word embeddings by training shallow neural networks to represent words in vector space.
  - Similar words have similar vectors in the high-dimensional space produced by Word2Vec.
  - Python Gensim and GoogleNews Vectors are suggested resources for working with Word2Vec.
  - Demonstrates operations such as vector similarity, vector arithmetic, and identifying odd words out with Word2Vec.
  - Further reading: [Gensim Word2Vec Tutorial](https://radimrehurek.com/gensim/auto_examples/tutorials/run_word2vec.html)

- **11.3 Part 11.3: What are Embedding Layers in Keras**
  - Embedding layers transform word indices into higher-dimensional numeric vectors to enrich neural network input.
  - Key parameters include `input_dim` (vocabulary size), `output_dim` (vector length), and `input_length` (input sequence length).
  - Shows examples of simple embedding layers, transferring hardcoded embeddings like one-hot encodings, and training embeddings.
  - Demonstrates a neural network classifying restaurant reviews into positive/negative with learned embeddings and dense layers.
  - Further reading: [Keras Embedding Layer Guide](https://keras.io/api/layers/core_layers/embedding/)

- **11.4 Part 11.4: Natural Language Processing with Spacy and Keras**
  - Explains word-level text generation with LSTM neural networks trained using Spacy tokenization of the Treasure Island text.
  - Details sequence creation, vectorization into one-hot encoded arrays, and training of the LSTM to predict next words.
  - Introduces temperature as a parameter controlling randomness versus conservatism in generated text.
  - Provides example outputs showing increasingly coherent text generated after training epochs.
  - Further reading: [Deep Learning for NLP with Keras](https://blog.keras.io/a-ten-minute-introduction-to-sequence-to-sequence-learning-in-keras.html)

- **11.5 Part 11.5: Learning English from Scratch with Keras and TensorFlow**
  - Introduces End-to-End Memory Networks used to train a neural network to read and answer questions about stories.
  - Uses the Facebook bAbI dataset, containing stories, queries, and answers, for training and evaluating the network.
  - Discusses data parsing, tokenization, vocabulary building, and vectorization to prepare input sequences, queries, and answers.
  - Details the neural network architecture with embedding layers, dot products, LSTM processing, and softmax classification.
  - Reports training results with accuracy up to 95.6% and demonstrates ad hoc querying using the trained model.
  - Further reading: [Facebook bAbI Dataset](https://research.fb.com/downloads/babi/) | [Keras Memory Networks Example](https://github.com/keras-team/keras/blob/master/examples/babi_rnn.py)
