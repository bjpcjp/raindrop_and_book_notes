<div class="nav">

⟵ [Up](index.html)  \|  [Index](index.html)

</div>

# pytorch

<div class="cards">

<div class="card">

<div class="card-title">

[PyTorch in One Hour: From Tensors to Training Neural Networks on
Multiple GPUs](https://sebastianraschka.com/teaching/pytorch-1h/)

</div>

<div class="card-image">

[![](https://sebastianraschka.com/images/teaching/pytorch-1h/hero.png)](https://sebastianraschka.com/teaching/pytorch-1h/)

</div>

A curated introduction to PyTorch that gets you up to speed in about an
hour.

</div>

<div class="card">

<div class="card-title">

[Meta Introduces KernelLLM: An 8B LLM that Translates PyTorch Modules
into Efficient Triton GPU
Kernels](https://www.marktechpost.com/2025/05/20/meta-introduces-kernelllm-an-8b-llm-that-translates-pytorch-modules-into-efficient-triton-gpu-kernels/)

</div>

<div class="card-image">

[![](https://www.marktechpost.com/wp-content/uploads/2025/05/llm_performance_comparison-scaled.png)](https://www.marktechpost.com/2025/05/20/meta-introduces-kernelllm-an-8b-llm-that-translates-pytorch-modules-into-efficient-triton-gpu-kernels/)

</div>

</div>

<div class="card">

<div class="card-title">

[Introducing the New PyTorch Landscape: Your Guide to the PyTorch
Ecosystem](https://pytorch.org/blog/pytorch-landscape/)

</div>

<div class="card-image">

[![](https://pytorch.org/assets/images/social-share.jpg)](https://pytorch.org/blog/pytorch-landscape/)

</div>

We’re excited to reveal our brand new PyTorch Landscape. The PyTorch
Landscape helps researchers, developers, and organizations easily locate
useful, curated, community-built tools that augment the PyTorch core
framework.

</div>

<div class="card">

<div class="card-title">

[Why PyTorch Gets All the
Love](https://thenewstack.io/why-pytorch-gets-all-the-love/)

</div>

<div class="card-image">

[![](https://cdn.thenewstack.io/media/2024/11/5aae1c0e-pytorch-love.jpg)](https://thenewstack.io/why-pytorch-gets-all-the-love/)

</div>

PyTorch has emerged as a top choice for researchers and developers due
to its relative ease of use and continuing improvement in performance.

</div>

<div class="card">

<div class="card-title">

[PyTorch 101, Understanding Graphs, Automatic Differentiation and
Autograd](https://www.digitalocean.com/community/tutorials/pytorch-101-understanding-graphs-and-automatic-differentiation)

</div>

<div class="card-image">

[![](https://www.digitalocean.com/_next/static/media/intro-to-cloud.d49bc5f7.jpeg)](https://www.digitalocean.com/community/tutorials/pytorch-101-understanding-graphs-and-automatic-differentiation)

</div>

In this article, we dive into how PyTorch’s Autograd engine performs
automatic differentiation.

</div>

<div class="card">

<div class="card-title">

[Triton Kernel Compilation
Stages](https://pytorch.org/blog/triton-kernel-compilation-stages/)

</div>

<div class="card-image">

[![](https://pytorch.org/assets/images/social-share.jpg)](https://pytorch.org/blog/triton-kernel-compilation-stages/)

</div>

The Triton open-source programming language and compiler offers a
high-level, python-based approach to create efficient GPU code. In this
blog, we highlight the underlying details of how a triton program is
compiled and the intermediate representations. For an introduction to
Triton, we refer readers to this blog.

</div>

<div class="card">

<div class="card-title">

[PyTorch 2.5 Released: Advancing Machine Learning Efficiency and
Scalability](https://www.marktechpost.com/2024/10/17/pytorch-2-5-released-advancing-machine-learning-efficiency-and-scalability/)

</div>

<div class="card-image">

[![](https://www.marktechpost.com/wp-content/uploads/2024/10/Screenshot-2024-10-17-at-3.34.05-PM.png)](https://www.marktechpost.com/2024/10/17/pytorch-2-5-released-advancing-machine-learning-efficiency-and-scalability/)

</div>

The PyTorch community has continuously been at the forefront of
advancing machine learning frameworks to meet the growing needs of
researchers, data scientists, and AI engineers worldwide. With the
latest PyTorch 2.5 release, the team aims to address several challenges
faced by the ML community, focusing primarily on improving computational
efficiency, reducing start up times, and enhancing performance
scalability for newer hardware. In particular, the release targets
bottlenecks experienced in transformer models and LLMs (Large Language
Models), the ongoing need for GPU optimizations, and the efficiency of
training and inference for both research and production settings. These
updates help PyTorch

</div>

<div class="card">

<div class="card-title">

[FlexAttention: The Flexibility of PyTorch with the Performance of
FlashAtte](https://pytorch.org/blog/flexattention)

</div>

<div class="card-image">

[![](https://pytorch.org/assets/images/social-share.jpg)](https://pytorch.org/blog/flexattention)

</div>

</div>

<div class="card">

<div class="card-title">

[FlashAttention-3: Fast and Accurate Attention with Asynchrony and
Low-preci](https://pytorch.org/blog/flashattention-3)

</div>

<div class="card-image">

[![](https://pytorch.org/assets/images/social-share.jpg)](https://pytorch.org/blog/flashattention-3)

</div>

Attention, as a core layer of the ubiquitous Transformer architecture,
is a bottleneck for large language models and long-context applications.
FlashAttention (and FlashAttention-2) pioneered an approach to speed up
attention on GPUs by minimizing memory reads/writes, and is now used by
most libraries to accelerate Transformer training and inference. This
has contributed to a massive increase in LLM context length in the last
two years, from 2-4K (GPT-3, OPT) to 128K (GPT-4), or even 1M (Llama 3).
However, despite its success, FlashAttention has yet to take advantage
of new capabilities in modern hardware, with FlashAttention-2 achieving
only 35% utilization of theoretical max FLOPs on the H100 GPU. In this
blogpost, we describe three main techniques to speed up attention on
Hopper GPUs: exploiting asynchrony of the Tensor Cores and TMA to (1)
overlap overall computation and data movement via warp-specialization
and (2) interleave block-wise matmul and softmax operations, and (3)
incoherent processing that leverages hardware support for FP8
low-precision.

</div>

<div class="card">

<div class="card-title">

[This Is How To Optimize PyTorch for Faster Model
Training](https://thenewstack.io/this-is-how-to-optimize-pytorch-for-faster-model-training)

</div>

<div class="card-image">

[![](https://cdn.thenewstack.io/media/2024/07/e46806ae-traffic-332857_1280.jpg)](https://thenewstack.io/this-is-how-to-optimize-pytorch-for-faster-model-training)

</div>

These six tips will help you significantly accelerate your model
training.

</div>

<div class="card">

<div class="card-title">

[Comprehensive Guide to Datasets and Dataloaders in
PyTorch](https://towardsdatascience.com/comprehensive-guide-to-datasets-and-dataloaders-in-pytorch-4d20f973d5d5?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*poblxhms3Asf992XLDnNfg.png)](https://towardsdatascience.com/comprehensive-guide-to-datasets-and-dataloaders-in-pytorch-4d20f973d5d5?source=rss----7f60cf5620c9---4)

</div>

The full guide to creating custom datasets and dataloaders for different
models in PyTorch

</div>

<div class="card">

<div class="card-title">

[Understanding Principal Component Analysis in
PyTorch](https://towardsdatascience.com/differentiable-principal-component-analysis-in-pytorch-using-power-iteration-ee93ac9fa2c4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1192/1*bLWUKmsBU0wi080CUgEhxA.png)](https://towardsdatascience.com/differentiable-principal-component-analysis-in-pytorch-using-power-iteration-ee93ac9fa2c4)

</div>

Built-in function vs. numerical methods

</div>

<div class="card">

<div class="card-title">

[How AMD May Get Across the CUDA
Moat](https://www.hpcwire.com/2023/10/05/how-amd-may-get-across-the-cuda-moat)

</div>

<div class="card-image">

[![](https://www.hpcwire.com/wp-content/uploads/2023/10/AMD-MI300A.png)](https://www.hpcwire.com/2023/10/05/how-amd-may-get-across-the-cuda-moat)

</div>

When discussing GenAI, the term "GPU" almost always enters the
conversation and the topic often moves toward performance and access.
Interestingly, the word "GPU" is assumed to mean "Nvidia" products. (As
an aside, the popular Nvidia hardware used in GenAI are not
technically...

</div>

<div class="card">

<div class="card-title">

[Inside the Matrix: Visualizing Matrix Multiplication, Attention and
Beyond](https://pytorch.org/blog/inside-the-matrix)

</div>

<div class="card-image">

[![](https://pytorch.org/assets/images/social-share.jpg)](https://pytorch.org/blog/inside-the-matrix)

</div>

Use 3D to visualize matrix multiplication expressions, attention heads
with real weights, and more.

</div>

<div class="card">

<div class="card-title">

[PyTorch Model Performance Analysis and Optimization — Part
6](https://towardsdatascience.com/pytorch-model-performance-analysis-and-optimization-part-6-b87412a0371b?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*mY1zmXYnEfE44Pma)](https://towardsdatascience.com/pytorch-model-performance-analysis-and-optimization-part-6-b87412a0371b?source=rss----7f60cf5620c9---4)

</div>

How to Identify and Analyze Performance Issues in the Backward Pass with
PyTorch Profiler, PyTorch Hooks, and TensorBoard

</div>

<div class="card">

<div class="card-title">

[Accelerated CPU Inference with PyTorch Inductor using
torch.compile](https://pytorch.org/blog/accelerated-cpu-inference)

</div>

<div class="card-image">

[![](https://pytorch.org/assets/images/social-share.jpg)](https://pytorch.org/blog/accelerated-cpu-inference)

</div>

Story at a Glance

</div>

<div class="card">

<div class="card-title">

[Variational Autoencoder (VAE) with Discrete Distribution using Gumbel
Softm](https://towardsdatascience.com/variational-autoencoder-vae-with-discrete-distribution-using-gumbel-softmax-b3f749b3417e?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:640/1*IB22-8qoNpIITYqKA034lQ.png)](https://towardsdatascience.com/variational-autoencoder-vae-with-discrete-distribution-using-gumbel-softmax-b3f749b3417e?source=rss----7f60cf5620c9---4)

</div>

Theory and PyTorch Implementation

</div>

<div class="card">

<div class="card-title">

[Optimizing Memory Usage for Training LLMs and Vision Transformers in
PyTorc](https://lightning.ai/pages/community/tutorial/pytorch-memory-vit-llm)

</div>

<div class="card-image">

[![](https://lightningaidev.wpengine.com/wp-content/uploads/2023/07/pytorch-memory-hero.png)](https://lightning.ai/pages/community/tutorial/pytorch-memory-vit-llm)

</div>

This article provides a series of techniques that can lower memory
consumption in PyTorch (when training vision transformers and LLMs) by
approximately 20x without sacrificing modeling performance and
prediction accuracy.

</div>

<div class="card">

<div class="card-title">

[PyTorch 2.0: Our next generation release that is faster, more Pythonic
and Dynamic as ever](https://pytorch.org/blog/pytorch-2.0-release)

</div>

<div class="card-image">

[![](https://pytorch.org/assets/images/social-share.jpg)](https://pytorch.org/blog/pytorch-2.0-release)

</div>

We are excited to announce the release of PyTorch® 2.0 which we
highlighted during the PyTorch Conference on 12/2/22! PyTorch 2.0 offers
the same eager-mode development and user experience, while fundamentally
changing and supercharging how PyTorch operates at compiler level under
the hood with faster performance and support for Dynamic Shapes and
Distributed.

</div>

<div class="card">

<div class="card-title">

[Some Techniques To Make Your PyTorch Models Train
Faster](https://sebastianraschka.com/blog/2023/pytorch-faster.html)

</div>

<div class="card-image">

[![](https://sebastianraschka.com/images/blog/2023/pytorch-faster/hero.png)](https://sebastianraschka.com/blog/2023/pytorch-faster.html)

</div>

This blog post outlines techniques for improving the training
performance of your PyTorch model without compromising its accuracy. To
do so, we will wrap a P...

</div>

<div class="card">

<div class="card-title">

[Comparing Different Automatic Image Augmentation Methods in
PyTorch](https://sebastianraschka.com/blog/2023/data-augmentation-pytorch.html)

</div>

<div class="card-image">

[![](https://sebastianraschka.com/images/blog/2023/data-augmentation-pytorch/hero.jpg)](https://sebastianraschka.com/blog/2023/data-augmentation-pytorch.html)

</div>

Data augmentation is a key tool in reducing overfitting, whether it's
for images or text. This article compares three Auto Image Data
Augmentation techniques...

</div>

<div class="card">

<div class="card-title">

[Torch and Torchvision C installation and debugging on
Linux](https://towardsdatascience.com/torch-and-torchvision-c-installation-and-debugging-on-linux-263676c38fa2)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:825/1*sdG0loJNkXjq83kB6_BAVg.png)](https://towardsdatascience.com/torch-and-torchvision-c-installation-and-debugging-on-linux-263676c38fa2)

</div>

Example debugging RoIAlign from Torchvision

</div>

<div class="card">

<div class="card-title">

[Why TensorFlow for Python is dying a slow
death](https://thenextweb.com/news/why-tensorflow-for-python-is-dying-a-slow-death)

</div>

<div class="card-image">

[![](https://img-cdn.tnwcdn.com/image/tnw-blurple?filter_last=1&fit=1280%2C640&url=https%3A%2F%2Fcdn0.tnwcdn.com%2Fwp-content%2Fblogs.dir%2F1%2Ffiles%2F2023%2F01%2FAdd-a-heading-1.jpg&signature=a59a25eca66453bf93e044239c29b88c)](https://thenextweb.com/news/why-tensorflow-for-python-is-dying-a-slow-death)

</div>

Many developers who use Python for machine learning are now switching to
PyTorch. Find out why and what the future could hold for TensorFlow.

</div>

<div class="card">

<div class="card-title">

[lucidrains/vit-pytorch: Implementation of Vision Transformer, a simple
way to achieve SOTA in vision classification with only a single
transformer encoder, in
Pytorch](https://github.com/lucidrains/vit-pytorch)

</div>

<div class="card-image">

[![](https://opengraph.githubassets.com/9edc731f2a99d5a99777494dd7aaa43716ebad2f0f59b90b9e38e48aaecebb2c/lucidrains/vit-pytorch)](https://github.com/lucidrains/vit-pytorch)

</div>

Implementation of Vision Transformer, a simple way to achieve SOTA in
vision classification with only a single transformer encoder, in
Pytorch - lucidrains/vit-pytorch

</div>

<div class="card">

<div class="card-title">

[Artificial Intelligence for Geospatial Analysis with Pytorch’s TorchGeo
(pa](https://towardsdatascience.com/artificial-intelligence-for-geospatial-analysis-with-pytorchs-torchgeo-part-3-7521131f30b1?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*vm3VRhTtsjgUTJWF)](https://towardsdatascience.com/artificial-intelligence-for-geospatial-analysis-with-pytorchs-torchgeo-part-3-7521131f30b1?source=rss----7f60cf5620c9---4)

</div>

An end-to-end deep learning geospatial segmentation project using
Pytorch and TorchGeo packages

</div>

<div class="card">

<div class="card-title">

[YOLOv5 PyTorch
Tutorial](https://exxactcorp.com/blog/Deep-Learning/YOLOv5-PyTorch-Tutorial)

</div>

<div class="card-image">

[![](https://images.contentstack.io/v3/assets/blt71da4c740e00faaa/blt2ccd3f8f98a1b20a/6359ac9faa5f5f55fdf2826b/EXX-Blog-pytorch-yolo5-tutorial.jpg)](https://exxactcorp.com/blog/Deep-Learning/YOLOv5-PyTorch-Tutorial)

</div>

The YOLO algorithm offers high detection speed and performance through
its one-forward propagation capability. In this tutorial, we will focus
on YOLOv5.

</div>

<div class="card">

<div class="card-title">

[How to Accelerate your PyTorch GPU Training with
XLA](https://towardsdatascience.com/how-to-accelerate-your-pytorch-training-with-xla-on-aws-3d599bc8f6a9)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*U3cCzkY7bhrJxvv-)](https://towardsdatascience.com/how-to-accelerate-your-pytorch-training-with-xla-on-aws-3d599bc8f6a9)

</div>

The Power of PyTorch/XLA and how Amazon SageMaker Training Compiler
Simplifies its use

</div>

<div class="card">

<div class="card-title">

[fastai/fastbook: The fastai book, published as Jupyter
Notebooks](https://github.com/fastai/fastbook)

</div>

<div class="card-image">

[![](https://opengraph.githubassets.com/56a56c5305ccb0a394ad19298d45fc62f19c1779b0334baebb1ce57415f0c7b0/fastai/fastbook)](https://github.com/fastai/fastbook)

</div>

The fastai book, published as Jupyter Notebooks.

</div>

<div class="card">

<div class="card-title">

[How Computational Graphs are Executed in
PyTorch](https://substack.com/redirect/e7484b15-7584-48b5-b946-7fe144ca3241?u=1135489)

</div>

<div class="card-image">

[![](https://pytorch.org/)](https://substack.com/redirect/e7484b15-7584-48b5-b946-7fe144ca3241?u=1135489)

</div>

Welcome to the last entry into understanding the autograd engine of
PyTorch series! If you haven’t read parts 1 & 2 check them now to
understand how PyTorch creates the computational graph for the backward
pass!

</div>

<div class="card">

<div class="card-title">

[How to Build an Image-Captioning Model in
Pytorch](https://towardsdatascience.com/how-to-build-an-image-captioning-model-in-pytorch-29b9d8fe2f8c?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*9chjZxFWwGxc0gDh)](https://towardsdatascience.com/how-to-build-an-image-captioning-model-in-pytorch-29b9d8fe2f8c?source=rss----7f60cf5620c9---4)

</div>

A detailed step-by-step explanation of how to build an image-captioning
model in Pytorch

</div>

<div class="card">

<div class="card-title">

[Taking Datasets, DataLoaders, and PyTorch’s New DataPipes for a
Spin](https://sebastianraschka.com/blog/2022/datapipes.html)

</div>

<div class="card-image">

[![](https://sebastianraschka.com/images/blog/2022/datapipes/card.png)](https://sebastianraschka.com/blog/2022/datapipes.html)

</div>

The PyTorch team recently announced TorchData, a prototype library
focused on implementing composable and reusable data loading utilities
for PyTorch. I hone...

</div>

<div class="card">

<div class="card-title">

[A Comprehensive Guide to Image Augmentation using
Pytorch](https://towardsdatascience.com/a-comprehensive-guide-to-image-augmentation-using-pytorch-fb162f2444be)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1000/0*kXJRrpkDPfjh6OqK)](https://towardsdatascience.com/a-comprehensive-guide-to-image-augmentation-using-pytorch-fb162f2444be)

</div>

A way to increase the amount of data and make the model more robust

</div>

<div class="card">

<div class="card-title">

[Introducing TorchRec, a library for modern production recommendation
system](https://pytorch.org/blog/introducing-torchrec)

</div>

<div class="card-image">

[![](https://pytorch.org/)](https://pytorch.org/blog/introducing-torchrec)

</div>

We are excited to announce TorchRec, a PyTorch domain library for
Recommendation Systems. This new library provides common sparsity and
parallelism primitives, enabling researchers to build state-of-the-art
personalization models and deploy them in production.

</div>

<div class="card">

<div class="card-title">

[Writing Custom Datasets, DataLoaders and Transforms — PyTorch Tutorials
2.4.0+cu121
documentation](https://pytorch.org/tutorials/beginner/data_loading_tutorial.html)

</div>

</div>

<div class="card">

<div class="card-title">

[Engineering Trade-Offs in Automatic Differentiation: from TensorFlow
and
Py](http://www.stochasticlifestyle.com/engineering-trade-offs-in-automatic-differentiation-from-tensorflow-and-pytorch-to-jax-and-julia)

</div>

<div class="card-image">

[![](https://www.stochasticlifestyle.com/wp-content/themes/chrisrack/style/faviPic2.PNG)](http://www.stochasticlifestyle.com/engineering-trade-offs-in-automatic-differentiation-from-tensorflow-and-pytorch-to-jax-and-julia)

</div>

To understand the differences between automatic differentiation
libraries, let’s talk about the engineering trade-offs that were made. I
would personally say that none of these libraries are “better” than
another, they simply all make engineering trade-offs based on the
domains and use cases they were aiming to satisfy. The easiest way to
describe these trade-offs is to follow the evolution and see how each
new library tweaked the trade-offs made of the previous. Early
TensorFlow used a graph building system, i.e. it required users to
essentially define variables in a specific graph language separate from
the host language. You had to define “TensorFlow variables” and
“TensorFlow ops”, and the AD would then be performed on this static
graph. Control flow constructs were limited to the constructs that could
be represented statically. For example, an \`ifelse\` function statement
is very different from ... READ MORE

</div>

<div class="card">

<div class="card-title">

[PyTorch vs TensorFlow in
2023](https://www.assemblyai.com/blog/pytorch-vs-tensorflow-in-2022)

</div>

<div class="card-image">

[![](https://www.assemblyai.com/blog/content/images/size/w1200/2023/01/pytorch_vs_tensorflow_2023.png)](https://www.assemblyai.com/blog/pytorch-vs-tensorflow-in-2022)

</div>

Should you use PyTorch vs TensorFlow in 2023? This guide walks through
the major pros and cons of PyTorch vs TensorFlow, and how you can pick
the right framework.

</div>

<div class="card">

<div class="card-title">

[An Introduction to PyTorch
Lightning](https://www.exxactcorp.com/blog/Deep-Learning/introduction-to-pytorch-lightning)

</div>

<div class="card-image">

[![](https://assets.exxactcorp.com/img/exx/misc/X-Exxact.svg)](https://www.exxactcorp.com/blog/Deep-Learning/introduction-to-pytorch-lightning)

</div>

PyTorch Lightning has opened many new possibilities in deep learning and
machine learning with a high level interface that makes it quicker to
work with PyTorch.

</div>

<div class="card">

<div class="card-title">

[The torch.linalg module: Accelerated Linear Algebra with Autograd in
PyTorch](https://pytorch.org/blog/torch-linalg-autograd)

</div>

<div class="card-image">

[![](https://pytorch.org/assets/images/cholesky-decomposition.png)](https://pytorch.org/blog/torch-linalg-autograd)

</div>

Linear algebra is essential to deep learning and scientific computing,
and it’s always been a core part of PyTorch. PyTorch 1.9 extends
PyTorch’s support for linear algebra operations with the torch.linalg
module. This module, documented here, has 26 operators, including faster
and easier to use versions of older PyTorch operators, every function
from NumPy’s linear algebra module extended with accelerator and
autograd support, and a few operators that are completely new. This
makes the torch.linalg immediately familiar to NumPy users and an
exciting update to PyTorch’s linear algebra support.

</div>

<div class="card">

<div class="card-title">

[Introduction - Hugging Face NLP
Course](https://huggingface.co/course/chapter1)

</div>

<div class="card-image">

[![](https://huggingface.co/front/thumbnails/learn/nlp-course.png)](https://huggingface.co/course/chapter1)

</div>

We’re on a journey to advance and democratize artificial intelligence
through open source and open science.

</div>

<div class="card">

<div class="card-title">

[29 Pytorch Snippets to Speed Up Your Machine Learning
Cycle](https://towardsdatascience.com/29-pytorch-snippets-to-speed-up-your-machine-learning-cycle-38e659e26b12?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*4vu8nj6_Ge9OBh2u)](https://towardsdatascience.com/29-pytorch-snippets-to-speed-up-your-machine-learning-cycle-38e659e26b12?source=rss----7f60cf5620c9---4)

</div>

From creating tensors to writing neural networks

</div>

<div class="card">

<div class="card-title">

[Pytorchvideo a deep learning library for video
understanding](https://ai.facebook.com/blog/pytorchvideo-a-deep-learning-library-for-video-understanding)

</div>

</div>

<div class="card">

<div class="card-title">

[An Introduction to PyTorch
Lightning](https://towardsdatascience.com/an-introduction-of-pytorch-lightning-230d03bcb262?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*x3i5Poku0ZpFzdHF)](https://towardsdatascience.com/an-introduction-of-pytorch-lightning-230d03bcb262?source=rss----7f60cf5620c9---4)

</div>

Word on the street is that PyTorch lightning is a much better version of
normal PyTorch. But what could it possibly have that it brought such
consensus in our world? Well, it helps researchers scale…

</div>

<div class="card">

<div class="card-title">

[Beginner guide to Variational Autoencoders (VAE) with PyTorch Lightning
(Part
2)](https://towardsdatascience.com/beginner-guide-to-variational-autoencoders-vae-with-pytorch-lightning-part-2-6b79ad697c79?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*eFzoUZatvbK4m3zK)](https://towardsdatascience.com/beginner-guide-to-variational-autoencoders-vae-with-pytorch-lightning-part-2-6b79ad697c79?source=rss----7f60cf5620c9---4)

</div>

This blog post is part of a mini-series that talks about the different
aspects of building a PyTorch Deep Learning project using Variational
Autoencoders. In Part 1, we looked at the variational…

</div>

<div class="card">

<div class="card-title">

[Using PyTorch + NumPy? You're making a
mistake.](https://tanelp.github.io/posts/a-bug-that-plagues-thousands-of-open-source-ml-projects)

</div>

A bug that plagues thousands of open-source ML projects.

</div>

<div class="card">

<div class="card-title">

[VISSL · A library for state-of-the-art self-supervised learning from
images](https://vissl.ai)

</div>

<div class="card-image">

[![](https://vissl.ai/img/vissllogo.svg)](https://vissl.ai)

</div>

A library for state-of-the-art self-supervised learning from images

</div>

<div class="card">

<div class="card-title">

[Image Feature Extraction Using
PyTorch](https://towardsdatascience.com/image-feature-extraction-using-pytorch-e3b327c3607a?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*P69zpl--JsVRSIVXL0hUzw.jpeg)](https://towardsdatascience.com/image-feature-extraction-using-pytorch-e3b327c3607a?source=rss----7f60cf5620c9---4)

</div>

Case Study: Image Clustering using K-Means Algorithm

</div>

<div class="card">

<div class="card-title">

[PyTorch Lightning Documentation — PyTorch Lightning 1.3.0dev
documentation](https://pytorch-lightning.readthedocs.io/en/latest)

</div>

</div>

<div class="card">

<div class="card-title">

[Using RAPIDS with
PyTorch](https://developer.nvidia.com/blog/using-rapids-with-pytorch)

</div>

<div class="card-image">

[![](https://developer-blogs.nvidia.com/wp-content/uploads/2021/01/RAPIDSPyTorch_Image1-1.jpg)](https://developer.nvidia.com/blog/using-rapids-with-pytorch)

</div>

In this post we take a look at how to use cuDF, the RAPIDS dataframe
library, to do some of the preprocessing steps required to get the
mortgage data in a format that PyTorch can process so that we…

</div>

<div class="card">

<div class="card-title">

[Custom C and CUDA Extensions — PyTorch Tutorials 1.7.0
documentation](https://pytorch.org/tutorials/advanced/cpp_extension.html)

</div>

</div>

<div class="card">

<div class="card-title">

[Semantic hand segmentation using
Pytorch](https://towardsdatascience.com/semantic-hand-segmentation-using-pytorch-3e7a0a0386fa?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:600/1*J_ZxnuUMcCQt_fxoG4ffOQ.gif)](https://towardsdatascience.com/semantic-hand-segmentation-using-pytorch-3e7a0a0386fa?source=rss----7f60cf5620c9---4)

</div>

Semantic segmentation is the task of predicting the class of each pixel
in an image. This problem is more difficult than object detection…

</div>

<div class="card">

<div class="card-title">

[Start Locally \| PyTorch](https://pytorch.org/get-started/locally)

</div>

<div class="card-image">

[![](https://pytorch.org/assets/images/social-share.jpg)](https://pytorch.org/get-started/locally)

</div>

</div>

<div class="card">

<div class="card-title">

[The Most Complete Guide to PyTorch for Data
Scientists](https://mlwhiz.com/blog/2020/09/09/pytorch_guide)

</div>

<div class="card-image">

[![](https://mlwhiz.com/images/pytorch_guide/main.png)](https://mlwhiz.com/blog/2020/09/09/pytorch_guide)

</div>

PyTorch has sort of became one of the de facto standards for creating
Neural Networks now, and I love its interface.

</div>

<div class="card">

<div class="card-title">

[PyTorch vs. TensorFlow – a detailed
comparison](https://www.tooploox.com/blog/pytorch-vs-tensorflow-a-detailed-comparison)

</div>

<div class="card-image">

[![](https://tooploox.com/wp-content/uploads/2020/10/Keras-vs.-Pytorch_COVER-1.jpg)](https://www.tooploox.com/blog/pytorch-vs-tensorflow-a-detailed-comparison)

</div>

Delve into the comprehensive comparison of PyTorch and TensorFlow, two
leading machine learning frameworks. This article covers vital
differences in ease of use, graph definition, and deployment
capabilities, including insights on transitioning from PyTorch to
TensorFlow Lite.

</div>

<div class="card">

<div class="card-title">

[Get Started With PyTorch With These 5 Basic
Functions.](https://towardsdatascience.com/get-started-with-pytorch-with-these-5-basic-functions-33ae428bab97?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*1eIJwJrtE6yL-2p7)](https://towardsdatascience.com/get-started-with-pytorch-with-these-5-basic-functions-33ae428bab97?source=rss----7f60cf5620c9---4)

</div>

As the ever-growing demand for deep learning continues to rise, more
developers and data scientists are joining the deep-learning…

</div>

<div class="card">

<div class="card-title">

[Matrix Operations Using PyTorch- A Beginner’s
Guide](https://medium.com/@sagnik2019/matrix-operations-using-pytorch-a-beginners-guide-d4ced61ea240)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*0SaBxURdGLX8bnMiRwnxAQ.png)](https://medium.com/@sagnik2019/matrix-operations-using-pytorch-a-beginners-guide-d4ced61ea240)

</div>

Application of different PyTorch functions on tensors

</div>

<div class="card">

<div class="card-title">

[Automate Your Neural Network Training With PyTorch
Lightning](https://medium.com/swlh/automate-your-neural-network-training-with-pytorch-lightning-1d7a981322d1)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*wxjsZuZyIGPvtEcZZDG7Uw.png)](https://medium.com/swlh/automate-your-neural-network-training-with-pytorch-lightning-1d7a981322d1)

</div>

PyTorch Lightning will automate your neural network training while
staying your code simple, clean and flexible. If you’re a researcher you

</div>

<div class="card">

<div class="card-title">

[Federated Learning using PyTorch and PySyft \|
LearnOpenCV](https://www.learnopencv.com/federated-learning-using-pytorch-and-pysyft)

</div>

<div class="card-image">

[![](https://learnopencv.com/wp-content/uploads/2020/05/asdasdsad-1.png)](https://www.learnopencv.com/federated-learning-using-pytorch-and-pysyft)

</div>

A gentle introduction to federated learning using PyTorch and PySyft
with the help of a real life example.

</div>

<div class="card">

<div class="card-title">

[Facebook AI, AWS partner to release new PyTorch
libraries](https://ai.facebook.com/blog/facebook-ai-aws-partner-to-release-new-pytorch-libraries-)

</div>

</div>

<div class="card">

<div class="card-title">

[Build PyTorch Models Easily Using
torchlayers](https://www.kdnuggets.com/2020/04/pytorch-models-torchlayers.html)

</div>

<div class="card-image">

[![](https://www.kdnuggets.com/wp-content/uploads/torchlayers-logo.jpg)](https://www.kdnuggets.com/2020/04/pytorch-models-torchlayers.html)

</div>

torchlayers aims to do what Keras did for TensorFlow, providing a
higher-level model-building API and some handy defaults and add-ons
useful for crafting PyTorch neural networks.

</div>

<div class="card">

<div class="card-title">

[\[P\] pytorch-optimizer -- collections of ready to use optimization
algorithm](https://www.reddit.com/r/MachineLearning/comments/fc3rgq/p_pytorchoptimizer_collections_of_ready_to_use)

</div>

<div class="card-image">

[![](https://share.redd.it/preview/post/fc3rgq)](https://www.reddit.com/r/MachineLearning/comments/fc3rgq/p_pytorchoptimizer_collections_of_ready_to_use)

</div>

249 votes, 21 comments. pytorch-optimizer -- collections of ready to use
optimization algorithms for PyTorch, includes: AccSGD, AdaBound, AdaMod…

</div>

<div class="card">

<div class="card-title">

[3D Deep Learning Made Easier — A Brief Introduction to Facebook’s
PyTorch3D](https://towardsdatascience.com/3d-deep-learning-made-easier-a-brief-introduction-to-facebooks-pytorch3d-framework-9fe3075f388a?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*I94v1tDDu4q_teZuFtlqZQ.png)](https://towardsdatascience.com/3d-deep-learning-made-easier-a-brief-introduction-to-facebooks-pytorch3d-framework-9fe3075f388a?source=rss----7f60cf5620c9---4)

</div>

Facebook released the PyTorch3D framework that supports deep learning in
3D environments. Find out what it is.

</div>

<div class="card">

<div class="card-title">

[From PyTorch to PyTorch Lightning — A gentle
introduction](https://towardsdatascience.com/from-pytorch-to-pytorch-lightning-a-gentle-introduction-b371b7caaf09?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:951/1*DgYiXo_5v3Zp68qGONosWw.png)](https://towardsdatascience.com/from-pytorch-to-pytorch-lightning-a-gentle-introduction-b371b7caaf09?source=rss----7f60cf5620c9---4)

</div>

This post walks through a side-by-side comparison of MNIST implemented
using both PyTorch and PyTorch Lightning.

</div>

<div class="card">

<div class="card-title">

[Building a strong baseline recommender using PyTorch, on a regular
laptop](https://towardsdatascience.com/how-to-build-a-strong-baseline-recommender-using-pytorch-on-a-regular-laptop-2ad497504fe6?source=rss----7f60cf5620c9---4)

</div>

</div>

<div class="card">

<div class="card-title">

[PyTorch internals](http://blog.ezyang.com/2019/05/pytorch-internals)

</div>

</div>

<div class="card">

<div class="card-title">

[BloodAxe/pytorch-toolbelt: PyTorch extensions for fast R&D prototyping
and Kaggle farming](https://github.com/BloodAxe/pytorch-toolbelt)

</div>

<div class="card-image">

[![](https://repository-images.githubusercontent.com/175851515/1b724d98-19b3-43e0-b1f2-9eda2c9bcc1e)](https://github.com/BloodAxe/pytorch-toolbelt)

</div>

PyTorch extensions for fast R&D prototyping and Kaggle farming -
BloodAxe/pytorch-toolbelt

</div>

<div class="card">

<div class="card-title">

[Tessellate-Imaging/Pytorch_Tutorial: A set of jupyter notebooks on
pytorch functions with
examples](https://github.com/Tessellate-Imaging/Pytorch_Tutorial)

</div>

<div class="card-image">

[![](https://opengraph.githubassets.com/8bdc259d9d9c6c16f0533f9c8ad0712b4b9fbdad01d3127e1ea1cfd7c1d5e86d/Tessellate-Imaging/Pytorch_Tutorial)](https://github.com/Tessellate-Imaging/Pytorch_Tutorial)

</div>

A set of jupyter notebooks on pytorch functions with examples -
Tessellate-Imaging/Pytorch_Tutorial

</div>

<div class="card">

<div class="card-title">

[kornia/kornia: Open Source Differentiable Computer Vision Library for
PyTor](https://github.com/kornia/kornia)

</div>

<div class="card-image">

[![](https://opengraph.githubassets.com/8a81c294c5ea98e4046a3a6041e3d0ff8f687b583209e0da0060187c75c9b4e9/kornia/kornia)](https://github.com/kornia/kornia)

</div>

Geometric Computer Vision Library for Spatial AI.

</div>

<div class="card">

<div class="card-title">

[PyTorch elastic training](https://github.com/pytorch/elastic)

</div>

<div class="card-image">

[![](https://opengraph.githubassets.com/6295d62a38ce6e83a50888071807d5c3c565da73577e61c7136b5b4473ff1c50/pytorch/elastic)](https://github.com/pytorch/elastic)

</div>

PyTorch elastic training.

</div>

<div class="card">

<div class="card-title">

<https://towardsdatascience.com/facebook-has-been-quietly-open-sourcing-some-amazing-deep-learning-capabilities-for-pytorch-a7ed5bc71f26>

</div>

</div>

<div class="card">

<div class="card-title">

[Welcome to PyTorch Tutorials — PyTorch Tutorials 1.3.0
documentation](https://pytorch.org/tutorials)

</div>

</div>

<div class="card">

<div class="card-title">

[(32) PyTorch Lightning - William Falcon -
YouTube](https://www.youtube.com/watch?app=desktop&feature=youtu.be&v=TM_jRrXYXxc)

</div>

<div class="card-image">

[![](https://i.ytimg.com/vi/TM_jRrXYXxc/maxresdefault.jpg)](https://www.youtube.com/watch?app=desktop&feature=youtu.be&v=TM_jRrXYXxc)

</div>

In recent years, techniques such as 16-bit precision, accumulated
gradients and distributed training have allowed models to train in
record times. In this talk William Falcon goes through the
implementation details of the 10 most useful of these techniques,
including DataLoaders, 16-bit precision, accumulated gradients and 4
different ways of distributing model training across hundreds of GPUs.
We’ll also show how to use these already built-in in PyTorch Lightning,
a Keras-like framework for ML researchers. William is the creator of
PyTorch-Lightning and an AI PhD student at Facebook AI Research and NYU
CILVR lab advised by Kyunghyun Cho. Before his PhD, he Co-founded AI
startup NextGenVest (acquired by Commonbond). He also spent time at
Goldman Sachs and Bonobos. He received his BA in Stats/CS/Math from
Columbia University. Every month the deep learning community of New York
gathers at the AWS loft to share discoveries and achievements and
describe new techniques.
https://github.com/williamFalcon/pytorch-lightning

</div>

<div class="card">

<div class="card-title">

[Deep Learning with PyTorch: A 60 Minute Blitz — PyTorch Tutorials
2.4.0+cu121
documentation](http://pytorch.org/tutorials/beginner/deep_learning_60min_blitz.html)

</div>

</div>

<div class="card">

<div class="card-title">

[Getting Started with PyTorch Part 1: Understanding How Automatic
Differenti](https://www.kdnuggets.com/2018/04/getting-started-pytorch-understanding-automatic-differentiation.html)

</div>

PyTorch has emerged as a major contender in the race to be the king of
deep learning frameworks. What makes it really luring is it’s dynamic
computation graph paradigm.

</div>

<div class="card">

<div class="card-title">

[PyTorch Tensor
Basics](https://www.kdnuggets.com/2018/05/pytorch-tensor-basics.html)

</div>

This is an introduction to PyTorch's Tensor class, which is reasonably
analogous to Numpy's ndarray, and which forms the basis for building
neural networks in PyTorch.

</div>

<div class="card">

<div class="card-title">

[PyTorch](http://pytorch.org)

</div>

<div class="card-image">

[![](https://pytorch.org/assets/images/social-share.jpg)](http://pytorch.org)

</div>

Run PyTorch locally or get started quickly with one of the supported
cloud platforms

</div>

<div class="card">

<div class="card-title">

[wiseodd/generative-models: Collection of generative models, e.g. GAN,
VAE i](https://github.com/wiseodd/generative-models)

</div>

<div class="card-image">

[![](https://opengraph.githubassets.com/1aa9038c88d36a24e73806f455bc5ce27d437e8b7eca9a1f82db3d67c7b91d75/wiseodd/generative-models)](https://github.com/wiseodd/generative-models)

</div>

Collection of generative models, e.g. GAN, VAE in Pytorch and
Tensorflow. - wiseodd/generative-models

</div>

<div class="card">

<div class="card-title">

[Highly Technical Reference Page: The Incredible
PyTorch](http://nuit-blanche.blogspot.com/2017/04/highly-technical-reference-page.html)

</div>

<div class="card-image">

[![](https://raw.githubusercontent.com/ritchieng/the-incredible-pytorch/master/the_incredible_pytorch.png)](http://nuit-blanche.blogspot.com/2017/04/highly-technical-reference-page.html)

</div>

A blog about Compressive Sensing, Computational Imaging, Machine
Learning. Using priors to avoid the curse of dimensionality arising in
Big Data.

</div>

<div class="card">

<div class="card-title">

[yunjey/pytorch-tutorial: PyTorch Tutorial for Deep Learning
Researchers](https://github.com/yunjey/pytorch-tutorial)

</div>

<div class="card-image">

[![](https://opengraph.githubassets.com/0f08c171bf4c8d86cd50702def34cb472ccb18a4e2d33125de297fb61c73a100/yunjey/pytorch-tutorial)](https://github.com/yunjey/pytorch-tutorial)

</div>

PyTorch Tutorial for Deep Learning Researchers.

</div>

</div>
