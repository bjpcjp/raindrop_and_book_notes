![ADNN-Apps-of-DNNs-Heaton](ADNN-Apps-of-DNNs-Heaton.best.png)

- **0.1 Introduction**
  - Deep learning is a group of technologies for neural networks that handle tabular data, images, text, and audio.
  - The course covers classic neural networks, CNN, LSTM, GRU, GAN, reinforcement learning, and HPC aspects such as GPU and grid computing.
  - Python with TensorFlow and Keras is used for implementation, assuming familiarity with at least one programming language.
  - Applications span computer vision, time series, security, NLP, and data generation.
  - Further reading: [Deep Learning by Goodfellow et al.](https://www.deeplearningbook.org/)

- **1 Python Preliminaries**
  - Introduces Python programming fundamentals and environment setup for deep learning.
  - Covers data structures like lists, dictionaries, sets, and JSON handling in Python.
  - Discusses file handling techniques including CSV, text, and image files.
  - Introduces functional programming constructs: functions, lambdas, map, filter, and reduce.
  - Provides guidelines on software installation and use of Jupyter Notebooks.
  - Further reading: [Python Official Documentation](https://docs.python.org/3/)

  - **1.1 Part 1.1: Course Overview**
    - Details course structure, grading, and assignment themes focused on deep learning applications.
    - Highlights instructor credentials and related resources.
    - Summarizes deep learning as efficient training of deep neural networks and its uses.
    - Explains machine learning differences from traditional software development.
    - Further reading: [Machine Learning Mastery](https://machinelearningmastery.com/)

  - **1.2 Part 1.2: Introduction to Python**
    - Covers basic Python syntax, variables, data types, printing, control flow, and loops.
    - Emphasizes the use of Python 3.x and differences from Python 2.x.
    - Demonstrates the use of indents for code blocks and basic string formatting.
    - Further reading: [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/)

  - **1.3 Part 1.3: Python Lists, Dictionaries, Sets and JSON**
    - Describes Python’s core collection types: lists (ordered, mutable), tuples (ordered, immutable), sets (unordered, no duplicates), and dictionaries (key-value pairs).
    - Illustrates list and tuple usage, mutability differences, and iteration techniques.
    - Explains sets for unique, unordered collections and dictionary operations including safe key access.
    - Introduces JSON as a hierarchical, semi-structured data format compatible with Python dictionaries and lists.
    - Provides examples of JSON parsing and generation in Python.
    - Further reading: [Python Data Structures](https://docs.python.org/3/tutorial/datastructures.html)

  - **1.4 Part 1.4: File Handling**
    - Explains handling various file types such as CSV, images, text, JSON, and audio in AI applications.
    - Demonstrates reading CSV files using Pandas and streaming large CSV files.
    - Shows reading text files line-by-line, supporting large file processing.
    - Introduces image loading and display using PIL and matplotlib in Python.
    - Details sources of data: local hard drive, internet URLs, and Google Drive.
    - Further reading: [Pandas Documentation](https://pandas.pydata.org/pandas-docs/stable/)

  - **1.5 Part 1.5: Functions, Lambdas, and Map/Reduce**
    - Covers defining and calling Python functions with named and default parameters.
    - Demonstrates string processing via functions and using map for applying functions over lists.
    - Introduces filter to select elements from collections conditionally.
    - Explains lambda expressions as anonymous functions to simplify code.
    - Details reduce for aggregating list elements into a single value.
    - Further reading: [Functional Programming HOWTO](https://docs.python.org/3/howto/functional.html)

- **2 Python for Machine Learning**
  - Introduces Pandas library as a primary tool for data manipulation and analysis in machine learning.
  - Demonstrates loading datasets into data frames and adjusting display options.
  - Explores computing descriptive statistics (mean, variance, standard deviation) for dataset fields.
  - Provides techniques for handling missing values by imputation (using median).
  - Covers removing outliers based on standard deviation thresholds to improve model quality.
  - Further reading: [10 Minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html)

  - **2.1 Part 2.1: Introduction to Pandas**
    - Defines the Pandas DataFrame as a tabular data structure used extensively for data preprocessing.
    - Uses the Auto MPG dataset as an example, accessible via online URL, to demonstrate DataFrame operations.
    - Shows methods to display data, configure output options, and compute basic statistics.
    - Illustrates identification and handling of missing values to maintain dataset integrity.
    - Introduces outlier detection by filtering rows with feature values beyond specified standard deviations.
    - Further reading: [Pandas User Guide](https://pandas.pydata.org/docs/user_guide/index.html)

  - **2.1.1 Missing Values**
    - Identifies missing values in datasets, specifically in the horsepower column of Auto MPG.
    - Replaces missing values with the column median to preserve dataset usability.
    - Notes alternative strategies like dropping rows with missing values.
    - Emphasizes the importance of handling missing data for accurate machine learning modeling.
    - Further reading: [Dealing with Missing Data](https://machinelearningmastery.com/handle-missing-data-python/)

  - **2.1.2 Dealing with Outliers**
    - Defines outliers as data points several standard deviations away from the mean.
    - Provides a function example to remove rows where feature values exceed specified deviation limits.
    - Highlights impact of outliers on data quality and model performance.
    - Recommends statistical methods for outlier detection before training.
    - Further reading: [Outlier Detection Techniques](https://scikit-learn.org/stable/modules/outlier_detection.html)
