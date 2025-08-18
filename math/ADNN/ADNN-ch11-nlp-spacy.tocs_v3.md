![ADNN-ch11-nlp-spacy](ADNN-ch11-nlp-spacy.best.png)

- **11.1 Part 11.1: Getting Started with Spacy in Python**
  - Focuses on word-level NLP using Spacy, preferred for its object abstraction of sentences.
  - Covers installation steps and handling of common errors such as missing language models.
  - Explains tokenization, part-of-speech tagging, and entity recognition using Spacy.
  - Demonstrates sentence diagramming and lemmatization functionality.
  - Introduces stop words and their treatment in natural language processing.
  - Further reading: [Spacy Official Documentation](https://spacy.io/usage)

- **11.2 Part 11.2: Word2Vec and Text Classification**
  - Describes Word2Vec as shallow two-layer neural networks that create word embeddings from text corpora.
  - Uses Python Gensim library to load pre-trained GoogleNews vectors and demonstrates finding word similarities.
  - Covers vector arithmetic for semantic relationships such as king - man + woman ≈ queen.
  - Provides example code for similarity and analogy tasks using Word2Vec.
  - Further reading: [Gensim Tutorials](https://radimrehurek.com/gensim/auto_examples/tutorials/run_word2vec.html)

- **11.3 Part 11.3: What are Embedding Layers in Keras**
  - Embedding layers map integer indexes into dense vectors, enabling richer data representations.
  - Clarifies key parameters: input_dim (vocabulary size), output_dim (vector size), and input_length.
  - Shows examples of creating, inspecting, and transferring embeddings including one-hot encoding.
  - Demonstrates training embeddings in a simple restaurant review classification model.
  - Embeddings allow the model to learn meaningful word representations during training.
  - Further reading: [Keras Embedding Layer Guide](https://keras.io/api/layers/core_layers/embedding/)

- **11.4 Part 11.4: Natural Language Processing with Spacy and Keras**
  - Combines Spacy tokenization with Keras LSTM models for word-level text generation.
  - Describes text preprocessing pipeline: downloading data, tokenizing, building vocabulary, and vectorization.
  - Uses one-hot encoding for input sequences to train a recurrent neural network.
  - Provides a sampling function to generate text from trained LSTM models with adjustable randomness (temperature).
  - Demonstrates generation of progressively more coherent text with training epochs.
  - Further reading: [Keras Text Generation Example](https://keras.io/examples/lstm_text_generation/)

- **11.5 Part 11.5: Learning English from Scratch with Keras and TensorFlow**
  - Introduces End-to-End Memory Networks for question answering using the Facebook bAbI dataset.
  - Presents utilities and functions to parse and preprocess stories and questions for training.
  - Describes vocabulary construction, vectorization of stories, queries, and answers.
  - Builds a custom model architecture including embeddings, dot products, permutations, LSTM, and dense layers.
  - Trains the model on single supporting fact tasks, achieving high accuracy (~95.6%) after extended epochs.
  - Allows adhoc querying on custom stories with vocabulary limitations.
  - Further reading: [bAbI Dataset](https://research.fb.com/downloads/babi/) and [Keras MemNets Example](https://blog.keras.io/keras-as-a-simplified-interface-to-tensorflow-tutorial.html)
