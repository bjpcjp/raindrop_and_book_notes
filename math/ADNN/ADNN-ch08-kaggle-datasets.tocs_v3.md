![ADNN-ch08-kaggle-datasets](ADNN-ch08-kaggle-datasets.best.png)

- **Chapter 8**
  - **8.1 Part 8.1: Introduction to Kaggle**
    - Kaggle hosts competitions where data scientists compete to create the best predictive models using provided datasets.  
    - The Titanic dataset is a tutorial used for learning, with no prizes and non-ranking scoring.  
    - The competition timeline may extend beyond initially scheduled dates.  
    - Further reading: [Kaggle Competitions](https://www.kaggle.com/competitions)  
  - **8.1.1 Kaggle Ranks**
    - Kaggle awards gold, silver, and bronze medals that contribute to user rankings.  
    - Various notable Kaggle user profiles and ranking systems are referenced.  
  - **8.1.2 Typical Kaggle Competition**
    - Competitions commonly include a summary page, data page, evaluation description, and leaderboard.  
  - **8.1.3 How Kaggle Competition Scoring**
    - Data is split into training and test sets; test labels are withheld.  
    - Public and private leaderboards evaluate partial test subsets but private scores are revealed only at competition end.  
    - Figure 8.1 illustrates the scoring process.  
  - **8.1.4 Preparing a Kaggle Submission**
    - Kaggle submissions consist of CSV files with row IDs and predicted labels or scores.  
    - Predictions must cover all test IDs without code submission.  
    - Multi-class problems require prediction columns per class.  
  - **8.1.5 Select Kaggle Competitions**
    - Popular tabular data competitions include Otto Group Product Classification and Predicting a Biological Response.  
    - Vision competitions include Diabetic Retinopathy Detection and Cats vs Dogs.  
  - **8.1.6 Module 8 Assignment**
    - The first assignment for this module is referenced as assignment 8.  

  - **8.2 Part 8.2: Building Ensembles with Scikit-Learn and Keras**
    - The section introduces feature importance methods and ensemble modeling techniques using popular ML libraries.  
    - Ensembles combine multiple models to improve prediction accuracy, a technique used frequently by Kaggle winners.  

    - **8.2.1 Evaluating Feature Importance**
      - Feature importance measures the predictive contribution of each input feature to a model.  
      - The input perturbation method, model-independent and from Breiman's random forest paper, is used here.  
      - Shuffling individual input columns degrades accuracy proportionally to their importance.  
      - The method uses log loss for classification and RMSE for regression.  
      - Further reading: [Accurate comparison of variable importance methods in ANNs](https://doi.org/10.1016/S0304-3800(03)00181-2)  

    - **8.2.2 Classification and Input Perturbation Ranking**
      - Demonstrates a classification neural network on the Iris dataset using TensorFlow Keras.  
      - Achieves perfect accuracy on the test split and ranks feature importance using input perturbation.  
      - Displays ranked feature importance with the petal length as most important.  

    - **8.2.3 Regression and Input Perturbation Ranking**
      - Applies input perturbation ranking to a regression network trained on the Auto MPG dataset.  
      - The highest-ranking feature in MPG prediction is displacement, followed by weight and horsepower.  
      - Model training shows iterative loss improvement through 100 epochs.  

    - **8.2.4 Biological Response with Neural Network**
      - Introduces a high-dimensional Kaggle biological response dataset (3751 samples, 1777 features).  
      - Constructs a classification neural network with early stopping to prevent overfitting.  
      - Validation accuracy reaches approximately 76%, with log loss reported for evaluation.  

    - **8.2.5 What Features/Columns are Important**
      - Uses input perturbation to rank the importance of thousands of features in the biological dataset.  
      - Top-ranked features significantly influence model prediction performance.  

    - **8.2.6 Neural Network Ensemble**
      - Ensembles neural network outputs with classical models like k-NN, random forests, extra trees, gradient boosting.  
      - Uses stratified K-Fold cross-validation for training and combines model predictions with logistic regression blending.  
      - Produces highly accurate predictions validated by log loss metrics across folds.  

  - **8.3 Part 8.3: Architecting Network: Hyperparameters**
    - Covers crucial hyperparameters influencing neural network design and training outcomes.  
    - Highlights the importance of choosing number of layers, neurons per layer, activation functions, and regularization.  

    - **8.3.1 Number of Hidden Layers and Neuron Counts**
      - Keras includes various layer types; dense layers fully connect neurons between layers.  
      - Dropout layers randomly zero inputs during training to reduce overfitting.  
      - Recommended neuron configuration is larger near input, shrinking towards output (triangular/trapezoid shape).  

    - **8.3.2 Activation Functions**
      - Common activations include RELU for hidden layers, softmax for classification outputs, and linear for regression outputs.  
      - Other activations include elu, selu, softplus, tanh, sigmoid, and exponential.  
      - Further reading: [Keras Activation Functions](https://keras.io/api/layers/activations/)  

    - **8.3.3 Advanced Activation Functions**
      - Advanced activations like LeakyReLU and PReLU contain trainable parameters to improve learning.  

    - **8.3.4 Regularization: L1, L2, Dropout**
      - Regularization techniques control model complexity and overfitting by adding penalty terms or zeroing activations.  
      - Further reading: [Keras Regularization](https://keras.io/api/layers/regularizers/) and [Keras Dropout](https://keras.io/api/layers/regularization_layers/dropout/)  

    - **8.3.5 Batch Normalization**
      - Normalizes layer activations to zero mean and unit variance per batch.  
      - Enables higher learning rates and faster convergence.  
      - Further reading: [Batch Normalization Paper](https://arxiv.org/abs/1502.03167)  

    - **8.3.6 Training Parameters**
      - Important parameters include batch size (commonly ~32) and learning rate (commonly ~1e-3).  
      - Choice of optimizer influences training dynamics.  
      - Further reading: [Keras Optimizers](https://keras.io/api/optimizers/)  

    - **8.3.7 Experimenting with Hyperparameters**
      - Demonstrates code to preprocess dataset, build networks, and systematically evaluate hyperparameter combinations.  
      - Uses stratified shuffle splitting and early stopping for training stability.  

  - **8.4 Part 8.4: Bayesian Hyperparameter Optimization for Keras**
    - Bayesian optimization efficiently searches hyperparameter space to find good network configurations, reducing exhaustive grid search overhead.  
    - Utilizes parameters: dropout rate, learning rate, neuron count percentage, and neuron shrink factor for network architecture.  
    - Demonstrates code generating a model that incrementally shrinks neuron counts per layer with dropout after each.  
    - Employs stratified K-fold cross-validation and early stopping in evaluation function.  
    - Uses the bayesian-optimization Python package to conduct optimization over defined bounds.  
    - Outputs improvement over random search and runtime metrics.  
    - Further reading: [Bayesian Optimization GitHub](https://github.com/fmfn/BayesianOptimization)  

  - **8.5 Part 8.5: Current Semester’s Kaggle**
    - Provides links and resources for the current and previous semesters’ Kaggle assignments for the course.  

    - **8.5.1 Iris as a Kaggle Competition**
      - Describes standard Kaggle files: train, test, and sample submission.  
      - Iris species labels are already index-encoded; test data excludes labels.  
      - Provides example code to train a neural network on iris train set, evaluate log loss, and generate a submission CSV.  

    - **8.5.2 MPG as a Kaggle Competition (Regression)**
      - Describes standard Kaggle files for the MPG dataset: train, test, and sample submission files.  
      - Shows building and training a regression neural network with early stopping and RMSE evaluation.  
      - Presents code to generate predictions on test data and write Kaggle submission CSV.  

    - **8.5.3 Module 8 Assignment**
      - The module 8 assignment reference is repeated.
