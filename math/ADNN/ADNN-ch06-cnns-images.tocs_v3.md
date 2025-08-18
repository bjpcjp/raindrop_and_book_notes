[ADNN-ch06-cnns-images](ADNN-ch06-cnns-images.best.png)

- **6.1 Part 6.1: Image Processing in Python**
  - Demonstrates using Pillow in Python to load, display, create, and transform images at the pixel level.
  - Covers standardizing images for uniform size and adding noise to images as preparation for autoencoder models.
  - Shows practical code examples for image loading from URLs and pixel manipulation.
  - Pillow enables image creation from 3D NumPy arrays specifying RGB values.
  - Further reading: [Pillow Documentation](https://pillow.readthedocs.io/en/stable/)

- **6.2 Part 6.2: Keras Neural Networks for Digits and Fashion MNIST**
  - Explains differences and similarities of neural networks when applied to computer vision tasks.
  - Introduces popular computer vision datasets: MNIST digits, Fashion-MNIST, and CIFAR (with CIFAR-10 and CIFAR-100 subsets).
  - Describes the CNN architecture including dense, convolution, max pooling, and dropout layers.
  - Provides detailed explanation of convolutional layers and max pooling hyperparameters and operations.
  - Presents TensorFlow/Keras code examples to load datasets, preprocess data, build, train, and evaluate CNN models.
  - Further reading: [CS231n Convolutional Neural Networks for Visual Recognition](http://cs231n.stanford.edu/)

  - **6.2.7 Convolutional Neural Networks (CNNs)**
    - CNNs simulate biological eye features by scanning overlapping input fields and respect spatial ordering.
    - They address challenges of scale, rotation, and noise in image recognition.
    - CNNs use specialized layers: dense, convolution, max pooling, and dropout for regularization.
    - Further reading: [LeNet-5 Paper](http://yann.lecun.com/exdb/lenet/)

  - **6.2.8 Convolution Layers**
    - Hyperparameters include number of filters, filter size, stride, padding, and activation function.
    - Filters scan the image spatially to detect visual features such as edges and color blobs.
    - The stride and padding control filter movement and output size, constrained by input dimensions.
    - Formula for output steps: steps = (w - f + 2p) / s + 1, where result must be integer.
    - Further reading: [Deep Learning Book, Chapter 9](https://www.deeplearningbook.org/)

  - **6.2.9 Max Pooling Layers**
    - Max pooling reduces spatial dimensions by taking max values within sliding windows.
    - Common hyperparameters are spatial extent (usually 2x2) and stride (typically 2), reducing data size by 75%.
    - Max pooling layers do not have trainable weights and serve as downsampling and regularization.
    - Further reading: [CS231n Pooling Notes](http://cs231n.github.io/convolutional-networks/#pool)

  - **6.2.11 Access to Data Sets - DIGITS**
    - Keras provides easy access to pre-split train/test MNIST datasets of 28x28 grayscale images.
    - Data shape details: x_train (60000, 28, 28), y_train (60000,), x_test (10000, 28, 28), y_test (10000,).
    - Examples demonstrate visualization and preparation for CNN modeling.

  - **6.2.12 Display the Digits**
    - MNIST digit images can be displayed as arrays or images using Matplotlib.
    - Random sampled images visualize dataset diversity.
    - Further reading: [MNIST Dataset](http://yann.lecun.com/exdb/mnist/)

  - **6.2.13 Training/Fitting CNN - DIGITS**
    - CNN models with Conv2D, MaxPooling2D, Dropout, Flatten, Dense layers are trained on MNIST.
    - Training typically takes longer on CPU than GPU.
    - Training outputs include loss and accuracy metrics per epoch with validation on test data.
    - Further reading: [Keras CNN Example](https://keras.io/examples/vision/mnist_convnet/)

  - **6.2.14 Evaluate Accuracy - DIGITS**
    - Model evaluation on full test dataset includes loss and accuracy outputs.
    - GPU prediction may require smaller batch sizes due to memory constraints.
    - Accuracy on MNIST test set can reach above 99%.
    - Further reading: [TensorFlow Model Evaluation](https://www.tensorflow.org/tutorials/keras/classification#evaluate_accuracy)

  - **6.2.15 MNIST Fashion**
    - Fashion-MNIST dataset is a 28x28 grayscale image set with 10 apparel categories.
    - Used as a drop-in replacement for original MNIST to benchmark machine learning algorithms.
    - Train/test split: 60000 training, 10000 testing images.
    - Further reading: [Fashion-MNIST GitHub](https://github.com/zalandoresearch/fashion-mnist)

  - **6.2.16 Display the Apparel**
    - Fashion-MNIST apparel images can be displayed similarly to MNIST digits.
    - Visualizations show pixel intensity data and class labels.
    - Further reading: [Fashion-MNIST Dataset Visualization](https://github.com/zalandoresearch/fashion-mnist#examples)

  - **6.2.17 Training/Fitting CNN - Fashion**
    - CNN model architecture mirrors MNIST digit classifier for Fashion-MNIST data.
    - Training achieves accuracy around 92-93% after multiple epochs.
    - Real-time data augmentation can be used to improve generalization.
    - Further reading: [Keras CNN Fashion-MNIST Example](https://keras.io/examples/vision/fashion_mnist_convnet/)

- **6.3 Part 6.3: Implementing a ResNet in Keras**
  - Residual learning enables training of very deep CNNs (up to 152 layers) by reformulating layers to learn residual functions.
  - ResNet model architectures include skip connections that allow identity mappings and improve gradient flow.
  - Keras provides two APIs: Sequential (simple linear stack) and Functional (supports complex architectures like ResNet).
  - CIFAR datasets often serve as benchmarks for ResNet training and evaluation.
  - Further reading: [He et al. ResNet Paper](https://arxiv.org/abs/1512.03385)

  - **6.3.2 CIFAR Dataset**
    - CIFAR-10 has 50,000 training images of size 32x32x3 categorized into 10 classes.
    - CIFAR-100 contains 100 classes arranged hierarchically.
    - Sample visualization shows diversity of image categories.
    - Further reading: [CIFAR Dataset Website](https://www.cs.toronto.edu/~kriz/cifar.html)

  - **6.3.3 ResNet V1**
    - ResNet V1 stacks of 2x(3x3) Conv-BatchNorm-ReLU layers with downsampling and doubling filters between stages.
    - Model depth must satisfy (depth - 2) mod 6 == 0, e.g. 20, 32, 44 layers.
    - Residual block skip connections use linear projection to match changed dimensions during downsampling.
    - Model ends with average pooling and dense softmax classifier.
    - Further reading: [ResNet V1 Implementation](https://keras.io/examples/cifar10_resnet/)

  - **6.3.4 ResNet V2**
    - ResNet V2 introduces full preactivation with BatchNorm-ReLU before convolutions and bottleneck layers.
    - Residual units use 1x1, 3x3, 1x1 convolutions within bottleneck blocks.
    - Model depth must satisfy (depth - 2) mod 9 == 0, e.g. 56, 110 layers.
    - The architecture improves gradient flow and training for deeper networks.
    - Further reading: [Identity Mappings in Deep Residual Networks](https://arxiv.org/abs/1603.05027)

  - **Training and Evaluation**
    - Training uses learning rate scheduling, data augmentation, and callbacks for optimization.
    - Data normalization by subtracting pixel mean improves accuracy.
    - Final evaluation on test data after hundreds of epochs shows validation loss and accuracy metrics.
    - Further reading: [ResNet Training Guide](https://keras.io/examples/cifar10_resnet/)

- **6.4 Part 6.4: Using Your Own Images with Keras**
  - Explains handling and preprocessing of custom image datasets for Keras CNNs.
  - Images must be normalized, resized, and optionally cropped or padded to uniform square sizes.
  - Data is formatted as 4D NumPy arrays (batch_size, height, width, channels) normalized to [-1, 1].
  - Saving training data in binary formats like NumPy’s .npy is preferable over CSV or Pickle for large image data.
  - Further reading: [TensorFlow Image Preprocessing Guide](https://www.tensorflow.org/tutorials/load_data/images)

- **6.5 Part 6.5: Recognizing Multiple Images with Darknet**
  - YOLO (You Only Look Once) enables detection and classification of multiple objects in a single image efficiently.
  - YOLO divides the image into an S x S grid and predicts bounding boxes with confidence scores and class probabilities for each cell.
  - The YOLO output tensor dimensions are S × S × (B · 5 + C), where B is bounding boxes per cell and C is quantity of classes.
  - Pretrained YOLO weights must be converted for TensorFlow usage; conversion is required only once.
  - YoloV3-TF2 is a TensorFlow 2.0 implementation; installation involves cloning from GitHub and downloading necessary files.
  - Further reading: [YOLO Website](https://pjreddie.com/darknet/yolo/), [YoloV3-TF2 GitHub](https://github.com/zzh8829/yolov3-tf2)

  - **6.5.5 Running DarkFlow (YOLO)**
    - YOLO is configured programmatically via Keras flags for weights, classes file, model options, and image size.
    - Device setup detects GPU availability and configures TensorFlow memory growth accordingly.
    - Weights are loaded into YOLO models (standard or tiny versions) once for repeated image inference.
    - Further reading: [TensorFlow GPU Guide](https://www.tensorflow.org/guide/gpu), [YOLOv3-TF2 Usage](https://github.com/zzh8829/yolov3-tf2)
