<div class="nav">

⟵ [Up](index.html)  \|  [Index](index.html)

</div>

# attention

<div class="cards">

<div class="card">

<div class="card-title">

[Topic 33: Slim Attention, KArAt, XAttention and Multi-Token Attention
Explained – What’s Really Changing in
Transformers?](https://huggingface.co/blog/Kseniase/attentions?fbclid=IwY2xjawJgrQhleHRuA2FlbQIxMQABHjZ2_OJkyTAVEb-K0wkUoq4VLTCrgIWQ4125yvu1GyuwHh6iHTCmJVAMstBF_aem_advNV4bDfVovH5jPMetwpQ)

</div>

<div class="card-image">

[![](https://cdn-thumbnails.huggingface.co/social-thumbnails/blog/Kseniase/attentions.png)](https://huggingface.co/blog/Kseniase/attentions?fbclid=IwY2xjawJgrQhleHRuA2FlbQIxMQABHjZ2_OJkyTAVEb-K0wkUoq4VLTCrgIWQ4125yvu1GyuwHh6iHTCmJVAMstBF_aem_advNV4bDfVovH5jPMetwpQ)

</div>

A Blog post by Ksenia Se on Hugging Face

</div>

<div class="card">

<div class="card-title">

[Why AI language models choke on too much
text](https://arstechnica.com/ai/2024/12/why-ai-language-models-choke-on-too-much-text/)

</div>

<div class="card-image">

[![](https://cdn.arstechnica.net/wp-content/uploads/2024/12/LLM-soup-1152x648.jpg)](https://arstechnica.com/ai/2024/12/why-ai-language-models-choke-on-too-much-text/)

</div>

Compute costs scale with the square of the input size. That’s not great.

</div>

<div class="card">

<div class="card-title">

[On MLA](https://planetbanatt.net/articles/mla.html)

</div>

<div class="card-image">

[![](https://planetbanatt.net/images/mla/manifold_perturbation.png)](https://planetbanatt.net/articles/mla.html)

</div>

</div>

<div class="card">

<div class="card-title">

[FlashSigmoid: A Hardware-Aware and Memory-Efficient Implementation of
Sigmoid Attention Yielding a
1](https://www.marktechpost.com/2024/09/13/flashsigmoid-a-hardware-aware-and-memory-efficient-implementation-of-sigmoid-attention-yielding-a-17-inference-kernel-speed-up-over-flashattention-2-on-h100-gpus)

</div>

<div class="card-image">

[![](https://www.marktechpost.com/wp-content/uploads/2024/09/Screenshot-2024-09-13-at-5.26.21-PM.png)](https://www.marktechpost.com/2024/09/13/flashsigmoid-a-hardware-aware-and-memory-efficient-implementation-of-sigmoid-attention-yielding-a-17-inference-kernel-speed-up-over-flashattention-2-on-h100-gpus)

</div>

Large Language Models (LLMs) have gained significant prominence in
modern machine learning, largely due to the attention mechanism. This
mechanism employs a sequence-to-sequence mapping to construct
context-aware token representations. Traditionally, attention relies on
the softmax function (SoftmaxAttn) to generate token representations as
data-dependent convex combinations of values. However, despite its
widespread adoption and effectiveness, SoftmaxAttn faces several
challenges. One key issue is the tendency of the softmax function to
concentrate attention on a limited number of features, potentially
overlooking other informative aspects of the input data. Also, the
application of SoftmaxAttn necessitates a row-wise reduction along the
input sequence length,

</div>

<div class="card">

<div class="card-title">

[Understanding Positional Embeddings in Transformers: From Absolute to
Rotar](https://towardsdatascience.com/understanding-positional-embeddings-in-transformers-from-absolute-to-rotary-31c082e16b26)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*EWz8ImltNHpDjMB8bOq_tQ.png)](https://towardsdatascience.com/understanding-positional-embeddings-in-transformers-from-absolute-to-rotary-31c082e16b26)

</div>

A deep dive into absolute, relative, and rotary positional embeddings
with code examples

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

[Deep Learning Architectures From CNN, RNN, GAN, and Transformers To
Encoder](https://www.marktechpost.com/2024/04/12/deep-learning-architectures-from-cnn-rnn-gan-and-transformers-to-encoder-decoder-architectures)

</div>

<div class="card-image">

[![](https://www.marktechpost.com/wp-content/uploads/2024/04/Hn6UWRfcQGS1sXgZTUWw6A.png)](https://www.marktechpost.com/2024/04/12/deep-learning-architectures-from-cnn-rnn-gan-and-transformers-to-encoder-decoder-architectures)

</div>

Deep learning architectures have revolutionized the field of artificial
intelligence, offering innovative solutions for complex problems across
various domains, including computer vision, natural language processing,
speech recognition, and generative models. This article explores some of
the most influential deep learning architectures: Convolutional Neural
Networks (CNNs), Recurrent Neural Networks (RNNs), Generative
Adversarial Networks (GANs), Transformers, and Encoder-Decoder
architectures, highlighting their unique features, applications, and how
they compare against each other. Convolutional Neural Networks (CNNs)
CNNs are specialized deep neural networks for processing data with a
grid-like topology, such as images. A CNN automatically detects the
important features without any human supervision.

</div>

<div class="card">

<div class="card-title">

[How Chain-of-Thought Reasoning Helps Neural Networks
Compute](https://www.quantamagazine.org/how-chain-of-thought-reasoning-helps-neural-networks-compute-20240321)

</div>

<div class="card-image">

[![](https://d2r55xnwy6nx47.cloudfront.net/uploads/2024/03/ChainOfThought-byNickSlater-Social.webp)](https://www.quantamagazine.org/how-chain-of-thought-reasoning-helps-neural-networks-compute-20240321)

</div>

Large language models do better at solving problems when they show their
work. Researchers are beginning to understand why.

</div>

<div class="card">

<div class="card-title">

[Von Restorff Effect: A Guaranteed Way to Capture
Attention](https://www.choicehacking.com/2024/03/03/von-restorff-effect-a-guaranteed-way-to-capture-attention)

</div>

<div class="card-image">

[![](https://www.choicehacking.com/wp-content/uploads/2024/05/Copy-of-Choice-Hacking-Podcast-Social-Image-Client-Logos-21.png)](https://www.choicehacking.com/2024/03/03/von-restorff-effect-a-guaranteed-way-to-capture-attention)

</div>

Brands spend millions every year tracking and analyzing what their
competition is doing. And it's not always so they can steal their
competition's best ideas. They know this surprising marketing truth:
When you do the opposite of what your competition is doing, you'll
capture more attention. Why does this work? It's down to a psychological

</div>

<div class="card">

<div class="card-title">

[Attention for Vision Transformers,
Explained](https://towardsdatascience.com/attention-for-vision-transformers-explained-70f83984c673?source=rss----7f60cf5620c9---4)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/da:true/resize:fit:1200/0*XLYx5OALyd914wu7)](https://towardsdatascience.com/attention-for-vision-transformers-explained-70f83984c673?source=rss----7f60cf5620c9---4)

</div>

The Math and the Code Behind Attention Layers in Computer Vision

</div>

<div class="card">

<div class="card-title">

[How do transformers work?+Design a Multi-class Sentiment Analysis for
Custo](https://open.substack.com/pub/nintyzeros/p/how-do-transformer-workdesign-a-multi)

</div>

<div class="card-image">

[![](https://substackcdn.com/image/fetch/w_1200,h_600,c_fill,f_jpg,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F1b143728-e85e-4a5e-af07-98662aa67d5a_727x1024.png)](https://open.substack.com/pub/nintyzeros/p/how-do-transformer-workdesign-a-multi)

</div>

We will deep dive into understanding how transformer model work like
BERT(Non-mathematical Explanation of course!). system design to use the
transformer to build a Sentiment Analysis

</div>

<div class="card">

<div class="card-title">

[Text vs. Images: Which Content Format is
Effective?](https://www.noupe.com/essentials/text-vs-images-which-content-format-is-effective.html)

</div>

<div class="card-image">

[![](https://www.noupe.com/wp-content/uploads/2024/02/yououijr0dw.jpg)](https://www.noupe.com/essentials/text-vs-images-which-content-format-is-effective.html)

</div>

When we talk about using different ways to share information, it's like
picking the one that fits what you need! Words, pictures, and mixes of
both have

</div>

<div class="card">

<div class="card-title">

[How to Seize Attention with the Secrets of a Sideshow
Barker](https://betterhumans.coach.me/how-to-seize-attention-with-the-secrets-of-a-sideshow-barker-6788fde4fd75)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:700/1*Y8itfAj5ZALVwzWq8kJlUQ.jpeg)](https://betterhumans.coach.me/how-to-seize-attention-with-the-secrets-of-a-sideshow-barker-6788fde4fd75)

</div>

Step right up!

</div>

<div class="card">

<div class="card-title">

[Medium](https://medium.com/re-form/how-to-pay-attention-4751adb53cb6%23.b773a2oo9)

</div>

</div>

<div class="card">

<div class="card-title">

[Grabbing Attention and Holding Onto
It](http://www.instigatorblog.com/grabbing-attention-and-holding-onto-it/2015/03/09)

</div>

</div>

<div class="card">

<div class="card-title">

[Why Washing Machines Are Learning to Play the
Harp](https://www.theatlantic.com/magazine/archive/2019/09/why-are-washing-machines-learning-to-play-the-harp/594706)

</div>

<div class="card-image">

[![](https://cdn.theatlantic.com/thumbor/8GRQi1Lln5V65qkbz9BswSUMt2Q=/0x43:2000x1085/1200x625/media/img/2019/07/DIS_Biz_Bliss_Sound/original.jpg)](https://www.theatlantic.com/magazine/archive/2019/09/why-are-washing-machines-learning-to-play-the-harp/594706)

</div>

Appliance makers believe more and better chimes, alerts, and jingles
make for happier customers. Are they right?

</div>

<div class="card">

<div class="card-title">

[How To Pay
Attention](https://medium.com/re-form/how-to-pay-attention-4751adb53cb6#.b773a2oo9)

</div>

<div class="card-image">

[![](https://miro.medium.com/v2/resize:fit:1200/1*5cWSOUarBjoLkXOK9jZwGA.png)](https://medium.com/re-form/how-to-pay-attention-4751adb53cb6#.b773a2oo9)

</div>

20 Ways To Win The War Against Seeing

</div>

<div class="card">

<div class="card-title">

[7 Techniques for Capturing People's
Attention](https://www.artofmanliness.com/articles/7-techniques-for-capturing-peoples-attention)

</div>

<div class="card-image">

[![](https://content.artofmanliness.com/uploads/2019/06/attention2.jpg)](https://www.artofmanliness.com/articles/7-techniques-for-capturing-peoples-attention)

</div>

The person who can capture and hold attention is the person who can
effectively influence human behavior. Here's how to do it.

</div>

<div class="card">

<div class="card-title">

[Why I changed my mind about advertising \| The Sample
blog](https://thesample.ai/blog/advertising)

</div>

<div class="card-image">

[![](https://obryant.dev/cards/33542b6fd643d2fc191b573cc2b7ce2c58dba074.png)](https://thesample.ai/blog/advertising)

</div>

I used to be very anti-advertising. Fast forward two years and several
pivots, and my slightly-less-early-stage business is doing \$900 per
month in revenue... from ads.

</div>

<div class="card">

<div class="card-title">

[Pay Attention: The Art of Noticing - Adobe
99U](https://99u.adobe.com/articles/67148/pay-attention-the-art-of-noticing-rob-walker)

</div>

</div>

<div class="card">

<div class="card-title">

[The Attention Diet](https://markmanson.net/attention-diet)

</div>

<div class="card-image">

[![](https://markmanson.net/wp-content/uploads/2019/06/attention-diet-cover-image.jpg)](https://markmanson.net/attention-diet)

</div>

Distractions have become so pervasive in the digital age that we've come
to accept them as normal. Here's how we can escape their grip and free
our minds a little.

</div>

</div>
