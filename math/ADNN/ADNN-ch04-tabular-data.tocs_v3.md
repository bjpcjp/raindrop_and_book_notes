[ADNN-ch04-tabular-data](ADNN-ch04-tabular-data.best.png)

- **4.1 Part 4.1: Encoding a Feature Vector for Keras Deep Learning**
  - Neural networks require numeric inputs formatted as feature vectors with one vector per data row.  
  - Categorical variables like "job" and "area" require conversion to dummy variables for neural network compatibility.  
  - Missing values in numeric columns (e.g., "income") are filled using median values or more advanced methods.  
  - The target column (e.g., "product") is separated from predictor columns, and IDs are excluded from inputs.  
  - [Dummy Variables in Pandas](https://pandas.pydata.org/docs/reference/api/pandas.get_dummies.html)  

- **4.1.1 Generate X and Y for a Classification Neural Network**
  - Predictors (X) are extracted as numpy arrays excluding target and ID columns.  
  - Targets (Y) are generated via one-hot encoded dummy variables for classification.  
  - Classification networks use output neurons equal to number of classes and softmax with categorical crossentropy loss.  
  - [Keras Multiclass Classification](https://keras.io/api/losses/probabilistic_losses/#categoricalcrossentropy-class)  

- **4.1.2 Generate X and Y for a Regression Neural Network**
  - Predictors (X) remain same as classification.  
  - Targets (Y) are numeric values directly from the dataset without dummy encoding.  
  - Regression neural networks use a single output neuron with linear activation and regression loss functions.  
  - [Keras Regression Models](https://keras.io/guides/writing_your_own_training_loop/)  

- **4.2 Part 4.2: Multiclass Classification with ROC and AUC**
  - Binary classification involves two classes with false positives and false negatives as key error types.  
  - ROC curves visualize classifier performance based on thresholds to balance sensitivity and specificity.  
  - Multiclass classification uses multiple output neurons and softmax to predict multiple classes.  
  - [ROC Curve Explanation](https://en.wikipedia.org/wiki/Receiver_operating_characteristic)  

- **4.2.1 Binary Classification and ROC Charts**
  - Confusion matrix displays true positives, true negatives, false positives, and false negatives for binary classification.  
  - Threshold choice affects trade-off between sensitivity (true positive rate) and specificity (true negative rate).  
  - ROC plots false positive rate vs true positive rate to measure classification quality with area under curve (AUC).  
  - [Khan Academy Sensitivity vs Specificity](https://www.khanacademy.org/test-prep/mcat/chemical-processes/biochemical-techniques/a/sensitivity-specificity-and-accuracy)  

- **4.2.2 ROC Chart Example**
  - Neural network model trained with Keras on breast cancer dataset using binary crossentropy loss.  
  - Early stopping is used to prevent overfitting by restoring best epoch weights.  
  - ROC curve plotted using sklearn's roc_curve and auc functions to evaluate model discrimination.  
  - [Scikit-Learn ROC Curve](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_curve.html)  

- **4.2.3 Multiclass Classification Error Metrics**
  - Multiclass classification neural networks use multiple output neurons with softmax activation.  
  - Error metrics include accuracy, log loss, and confusion matrices for performance evaluation.  
  - Standardization (z-score) is applied to numeric predictors before training.  
  - [Multiclass Classification Metrics](https://scikit-learn.org/stable/modules/model_evaluation.html#multiclass-and-multilabel-classification)  

- **4.2.4 Calculate Classification Accuracy**
  - Accuracy is the ratio of correctly predicted samples to total samples and is used only for classification.  
  - Predictions probabilities are converted to class indices using argmax before calculating accuracy.  
  - Higher accuracy values indicate better classification performance.  
  - [Sklearn Accuracy Score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.accuracy_score.html)  

- **4.2.5 Calculate Classification Log Loss**
  - Log loss penalizes incorrect predictions based on confidence, with lower values indicating better performance.  
  - Log loss accounts for predicted probabilities rather than hard classifications and is suited for binary classification.  
  - Neural networks output class probabilities used to compute log loss through negative log likelihood.  
  - [Log Loss Explanation](https://en.wikipedia.org/wiki/Loss_functions_for_classification#Cross-entropy_loss_function_and_logistic_loss)  

- **4.3 Part 4.3: Keras Regression for Deep Neural Networks with RMSE**
  - Regression neural networks predict numeric outputs using mean squared error (MSE) loss.  
  - RMSE is the square root of MSE and has the same unit as the target variable, making interpretation easier.  
  - Model training uses early stopping to restore weights from best validation loss epoch.  
  - Lift charts visualize predicted vs expected values sorted by outcome for evaluating regression performance.  
  - [Interpreting RMSE](https://en.wikipedia.org/wiki/Root-mean-square_deviation)  

- **4.3.1 Mean Square Error**
  - MSE calculates average squared difference between predicted and actual numerical values.  
  - Lower MSE values indicate better model fit but lack units matching the target variable.  
  - MSE serves as objective function for regression training in neural networks.  
  - [Mean Squared Error Definition](https://en.wikipedia.org/wiki/Mean_squared_error)  

- **4.3.2 Root Mean Square Error**
  - RMSE is the square root of MSE, providing error measurement in the original units of the target variable.  
  - RMSE is commonly used to evaluate regression models for interpretability.  
  - Lower RMSE values indicate closer predictions to actual target values.  
  - [Root Mean Square Error](https://en.wikipedia.org/wiki/Root-mean-square_deviation)  

- **4.3.3 Lift Chart**
  - Lift charts plot expected versus predicted values ordered by the target variable to assess regression accuracy.  
  - The proximity of predicted and expected lines indicates model accuracy across ranges of target values.  
  - Lift charts emphasize the model's strength or weakness in predicting different target value ranges.  
  - [Lift Chart Explanation](https://www.datasciencecentral.com/profiles/blogs/lift-charts-what-are-they-how-do-they-work)  

- **4.4 Part 4.4: Training Neural Networks**
  - Backpropagation adjusts neural network weights iteratively using gradients of the error function.  
  - Learning rate controls step size in gradient descent; too high or low values cause training issues.  
  - Momentum adds scaled previous weight changes to accelerate convergence and help escape local minima.  
  - Batch, online, and mini-batch training differ by how often weights are updated per training samples processed.  
  - Stochastic Gradient Descent (SGD) updates weights using random batches, offering efficiency and regularization.  
  - Advanced optimizers include Resilient Propagation, Nesterov Accelerated Gradient, Adagrad, Adadelta, and Adam.  
  - Adam optimizer uses adaptive estimates of first and second moments of gradients with bias correction.  
  - TensorFlow supports multiple optimizers: Adagrad, Adam, Ftrl, Momentum, RMSProp, and SGD.  
  - [Understanding Backpropagation](https://www.deeplearningbook.org/)  
  - [Adam Optimizer Paper](https://arxiv.org/abs/1412.6980)  

- **4.5 Part 4.5: Error Calculation from Scratch**
  - Manual calculation of MSE and RMSE is performed using squared differences and their average.  
  - Log loss for binary classification is computed using negative average log probability of correct predictions.  
  - Calculations demonstrate equivalence between standard libraries and manual methods.  
  - Log loss crucially penalizes confident wrong predictions more heavily than less confident ones.  
  - [Manual Error Calculation Guide](https://machinelearningmastery.com/how-to-calculate-log-loss-for-machine-learning/)
