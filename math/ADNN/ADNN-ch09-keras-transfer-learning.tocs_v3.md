[ADNN-ch09-keras-transfer-learning](ADNN-ch09-keras-transfer-learning.best.png)

- **9.1 Part 9.1: Introduction to Keras Transfer Learning**
  - Transfer learning begins training with pretrained weights rather than from scratch.
  - The pretrained network's top layers are removed and replaced for new classifications.
  - Transfer learning saves compute resources compared to training large neural networks.
  - The imagenet dataset contains quality pretrained models widely used for transfer learning.
  - Further reference: [Transfer Learning Guide by TensorFlow](https://www.tensorflow.org/tutorials/images/transfer_learning)

  - **9.1.1 Transfer Learning Example**
    - Demonstrates transferring layers from a neural network trained on the iris dataset.
    - The example clones and reuses layers to preserve learned weights and accuracy.
    - Only the final classification layer is replaced and trained with new flower classes.
    - First layers are frozen (non-trainable) to retain learned abstract features.
    - The approach enables efficient learning on new but related classification tasks.

  - **9.1.2 Module 9 Assignment**
    - Provides the initial assignment related to transfer learning.
    - Intended to reinforce practical understanding of transfer techniques.

- **9.2 Part 9.2: Popular Pretrained Neural Networks for Keras**
  - Lists major sources to find pretrained models, including TensorFlow Model Zoo and Papers with Code.
  - Keras includes built-in support for multiple state-of-the-art pretrained models.
  - Model options cover architectures for various trade-offs in accuracy and efficiency.

  - **9.2.1 DenseNet**
    - DenseNet connects each layer to every other layer in a feed-forward way.
    - This design alleviates vanishing gradients and encourages feature reuse.
    - DenseNets achieve state-of-the-art results on CIFAR-10, CIFAR-100, SVHN, and ImageNet.

  - **9.2.2 InceptionResNetV2 and InceptionV3**
    - Inception ResNet V2 is an advancement over Inception V3 combining ideas from ResNet.
    - Achieves new accuracy benchmarks in the ILSVRC image classification challenge.

  - **9.2.3 MobileNet**
    - MobileNet uses depth-wise separable convolutions for lightweight networks suited for mobile.
    - Includes hyperparameters to balance latency and accuracy depending on application needs.
    - Demonstrated strong performance on ImageNet and various embedded vision tasks.

  - **9.2.4 MobileNetV2**
    - Improves mobile model performance across multiple benchmarks and tasks.
    - Introduces SSDLite framework and Mobile DeepLabv3 for object detection and segmentation.

  - **9.2.5 NASNet**
    - NASNet learns network architectures on small datasets and transfers to larger datasets.
    - Achieves state-of-the-art accuracy on CIFAR-10 and ImageNet with fewer FLOPS required.
    - Introduces ScheduledDropPath regularization to improve generalization.

  - **9.2.6 ResNet, ResNetV2, ResNeXt**
    - Deep residual networks that enable training extremely deep architectures.
    - Uses identity mappings for improved forward and backward signal propagation.
    - Demonstrated improved results with very deep networks on CIFAR and ImageNet.

  - **9.2.7 VGG16 and VGG19**
    - Investigates convolutional network depth effects using small 3x3 filters.
    - Achieved top placements in ImageNet Challenge 2014 with 16-19 layer models.
    - Models generalize well to other datasets for image recognition.

  - **9.2.8 Xception**
    - Reinterprets Inception modules as extreme depthwise separable convolutions.
    - Architecture outperforms Inception V3 on ImageNet and larger classification datasets.
    - Gains attributed to more efficient parameter usage rather than increased capacity.

- **9.3 Part 9.3: Transfer Learning for Computer Vision and Keras**
  - Shows extending MobileNet pretrained on imagenet to classify custom media types.
  - Demonstrates importing MobileNet, removing top layers, adding new classification layers.
  - Freeze pretrained layers to only train new output layers for specialized tasks.
  - Uses Keras' flow_from_directory to efficiently handle image data loading.
  - Training achieves perfect accuracy on small, specialized four-class dataset with transfer learning.

  - **9.3.1 Transfer**
    - Discusses training image classification networks from scratch versus transfer learning.
    - Transfer learning enables leveraging pretrained lower-layer features for new data.
    - MobileNet's structure with many parameters is described for understanding transfer points.
    - Demonstrates code to classify sample images and to add and train custom layers.

- **9.4 Part 9.4: Transfer Learning for Languages and Keras**
  - Transfer learning is widely used in NLP for tasks like classification.
  - TensorFlow Hub supports pretrained language models usable in Keras.
  - Uses Universal Sentence Encoder and Google’s gnews-swivel-20dim embedding model.
  - Converts raw text inputs into dense, trainable vector embeddings.
  - Example classifies IMDb movie reviews into positive or negative sentiment with transfer learning.
  - Includes steps for model compilation, training, evaluation, and visualization.
  - Further reading: [Universal Sentence Encoder](https://arxiv.org/abs/1803.11175)

- **9.5 Part 9.5: Transfer Learning for Keras Feature Engineering**
  - Demonstrates extracting feature vectors from images using pretrained MobileNet.
  - Strips away dense layers to output convolutional layer results as feature vectors.
  - Resulting 1024-length vectors capture subcomponent image information.
  - These feature vectors may serve as input features for other ML models.
  - Provides code for image preprocessing, prediction, and model summary inspection.
