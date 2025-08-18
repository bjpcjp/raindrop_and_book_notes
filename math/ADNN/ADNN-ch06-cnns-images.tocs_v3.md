![ADNN-ch06-cnns-images](ADNN-ch06-cnns-images.best.png)

- **6.1 Part 6.1: Image Processing in Python**  
  - Demonstrates using Python's Pillow package to load, create, transform, and standardize images.  
  - Covers image creation from numpy arrays and pixel-level image manipulation, such as converting to grayscale.  
  - Introduces adding random noise to images to simulate real-world imperfections.  
  - Shows how to standardize images for consistent size and shape when processing multiple images.  
  - See also the [Pillow documentation](https://pillow.readthedocs.io/en/stable/).  

- **6.2 Part 6.2: Keras Neural Networks for Digits and Fashion MNIST**  
  - Focuses on CNN usage for computer vision tasks using popular datasets like MNIST digits and Fashion MNIST.  
  - Describes differences from traditional neural networks, including 3D input shape and layer types like convolution and max pooling.  
  - Introduces datasets CIFAR-10 and CIFAR-100 for experimental use.  
  - Explains convolutional layers and max pooling layers including hyperparameters and data dimensionality changes.  
  - Provides example code to load datasets, display samples, and build/train CNNs in Keras with results.  
  - External resource: [CS231n: Convolutional Neural Networks for Visual Recognition](http://cs231n.stanford.edu/).  

- **6.3 Part 6.3: Implementing a ResNet in Keras**  
  - Discusses residual learning to enable training of very deep networks via skip (residual) connections.  
  - Distinguishes Keras Sequential API from Functional API, recommending Functional API for complex models like ResNet.  
  - Provides details on CIFAR datasets and their use with ResNet.  
  - Implements ResNet layers and full ResNet V1 and V2 models with batch normalization and bottleneck layers.  
  - Explains learning rate schedules and real-time data augmentation to improve training.  
  - References: Original ResNet paper by He et al. (2015), and Identity Mappings in Deep Residual Networks (2016).  
  - Further reading: [Deep Residual Learning for Image Recognition](https://arxiv.org/abs/1512.03385).  

- **6.4 Part 6.4: Using Your Own Images with Keras**  
  - Describes loading, processing, and standardizing user-provided images for CNN training.  
  - Emphasizes making images square by cropping and resizing for consistent input dimensions.  
  - Demonstrates normalization of image pixel values to the range [-1, 1] to improve model performance.  
  - Discusses storage of preprocessed image datasets using NumPy's binary format instead of CSV due to dimensionality.  
  - Practical knowledge for preparing real-world images for neural network applications.  

- **6.5 Part 6.5: Recognizing Multiple Images with Darknet**  
  - Introduces YOLO (You Only Look Once), an efficient CNN for real-time object detection that predicts multiple bounding boxes per image grid cell.  
  - Explains output tensor dimensions with bounding box parameters and class confidences.  
  - Describes Python usage of YOLO via the YoloV3-TF2 package, including steps to install, obtain pretrained weights, and convert them for TensorFlow compatibility.  
  - Covers programmatic configuration of YOLO using Keras flags and GPU setup for performance.  
  - References: YOLO original papers and YoloV3-TF2 GitHub repository.  
  - Further reading: [YOLO: Real-Time Object Detection](https://pjreddie.com/darknet/yolo/).
