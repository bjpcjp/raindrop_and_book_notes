[ADNN-ch14-automl-autoencoders-anomaly](ADNN-ch14-automl-autoencoders-anomaly.best.png)

- **14.1 Part 14.1: What is AutoML**  
  - AutoML automates model generation by processing raw data inputs without manual intervention.  
  - Several commercial AutoML applications exist, including Rapid Miner, Dataiku, DataRobot, and H2O Driverless.  
  - Google Cloud offers AutoML services with tutorials for usage.  
  - A simple AutoML system includes automated CSV reading, feature analysis, encoding determination, and neural network training.  
  - Example code demonstrates data transformation, encoding, and neural network cross-validation.  

- **14.2 Part 14.2: Using Denoising AutoEncoders in Keras**  
  - Function approximation uses neural networks to model complex relationships such as sine functions via regression.  
  - Neural networks support multi-output regression, predicting multiple continuous outputs from the same input.  
  - Autoencoders compress input data into a lower-dimensional representation and reconstruct inputs from this encoding.  
  - Image autoencoders process and reconstruct images, with preprocessing to standardize size and shape.  
  - Denoising autoencoders train on noisy inputs to recover original clean data, improving noise robustness.  
  - Code examples cover image preprocessing, noise addition, training, and visualizing denoising results.  
  - Further reading: [Denoising Autoencoders](https://www.cs.toronto.edu/~hinton/absps/guideTR.pdf)  

- **14.3 Part 14.3: Anomaly Detection in Keras**  
  - Anomaly detection identifies data that deviates significantly from training data patterns without labeled targets.  
  - The KDD-99 dataset is a commonly used benchmark for intrusion detection and anomaly detection.  
  - The dataset requires preprocessing including Z-score normalization of numeric features and dummy encoding of categorical features.  
  - Normal and attack subsets enable training autoencoders to learn normal behavior and detect anomalies via reconstruction error.  
  - Experiments show significantly higher RMSE error on attack data, indicating successful anomaly detection.  
  - Further reading: [KDD Cup 1999 Data](http://kdd.ics.uci.edu/databases/kddcup99/kddcup99.html)  

- **14.4 Part 14.4: Training an Intrusion Detection System with KDD99**  
  - The KDD-99 dataset remains a standard for training and evaluating network intrusion detection systems (IDS).  
  - Reading KDD-99 involves adding column headers and analyzing feature distributions for preprocessing.  
  - Numeric columns are encoded as Z-scores; categorical columns are converted to dummy variables for compatibility with neural networks.  
  - Training a neural network classifier on KDD-99 predicts attack types and normal network behavior with high accuracy.  
  - Early stopping and validation data ensure model generalization during extended training epochs.  
  - Further reading: [Intrusion Detection Using Neural Networks](https://www.sciencedirect.com/science/article/pii/S1877050916306951)
