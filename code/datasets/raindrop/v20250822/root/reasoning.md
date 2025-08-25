<div class="nav">

⟵ [Up](index.html)  \|  [Index](index.html)

</div>

# reasoning

<div class="cards">

<div class="card">

<div class="card-title">

[Hierarchical Reasoning Model](https://arxiv.org/abs/2506.21734)

</div>

<div class="card-image">

[![](https://arxiv.org/static/browse/0.3.4/images/arxiv-logo-fb.png)](https://arxiv.org/abs/2506.21734)

</div>

Reasoning, the process of devising and executing complex goal-oriented
action sequences, remains a critical challenge in AI. Current large
language models (LLMs) primarily employ Chain-of-Thought (CoT)
techniques, which suffer from brittle task decomposition, extensive data
requirements, and high latency. Inspired by the hierarchical and
multi-timescale processing in the human brain, we propose the
Hierarchical Reasoning Model (HRM), a novel recurrent architecture that
attains significant computational depth while maintaining both training
stability and efficiency. HRM executes sequential reasoning tasks in a
single forward pass without explicit supervision of the intermediate
process, through two interdependent recurrent modules: a high-level
module responsible for slow, abstract planning, and a low-level module
handling rapid, detailed computations. With only 27 million parameters,
HRM achieves exceptional performance on complex reasoning tasks using
only 1000 training samples. The model operates without pre-training or
CoT data, yet achieves nearly perfect performance on challenging tasks
including complex Sudoku puzzles and optimal path finding in large
mazes. Furthermore, HRM outperforms much larger models with
significantly longer context windows on the Abstraction and Reasoning
Corpus (ARC), a key benchmark for measuring artificial general
intelligence capabilities. These results underscore HRM's potential as a
transformative advancement toward universal computation and
general-purpose reasoning systems.

</div>

<div class="card">

<div class="card-title">

[The State of Reinforcement Learning for LLM
Reasoning](https://sebastianraschka.com/blog/2025/the-state-of-reinforcement-learning-for-llm-reasoning.html)

</div>

<div class="card-image">

[![](https://sebastianraschka.com/images/blog/2025/the-state-of-reinforcement-learning-for-llm-reasoning/hero.jpg)](https://sebastianraschka.com/blog/2025/the-state-of-reinforcement-learning-for-llm-reasoning.html)

</div>

A lot has happened this month, especially with the releases of new
flagship models like GPT-4.5 and Llama 4. But you might have noticed
that reactions to these releases were relatively muted. Why? One reason
could be that GPT-4.5 and Llama 4 remain conventional models, which
means they were trained without explicit reinforcement learning for
reasoning. However, OpenAI's recent release of the o3 reasoning model
demonstrates there is still considerable room for improvement when
investing compute strategically, specifically via reinforcement learning
methods tailored for reasoning tasks. While reasoning alone isn't a
silver bullet, it reliably improves model accuracy and problem-solving
capabilities on challenging tasks (so far). And I expect
reasoning-focused post-training to become standard practice in future
LLM pipelines. So, in this article, let's explore the latest
developments in reasoning via reinforcement learning.

</div>

<div class="card">

<div class="card-title">

[First Look at Reasoning From Scratch: Chapter
1](https://sebastianraschka.com/blog/2025/first-look-at-reasoning-from-scratch.html)

</div>

<div class="card-image">

[![](https://sebastianraschka.com/images/blog/2025/first-look-at-reasoning-from-scratch/hero.jpg)](https://sebastianraschka.com/blog/2025/first-look-at-reasoning-from-scratch.html)

</div>

As you know, I've been writing a lot lately about the latest research on
reasoning in LLMs. Before my next research-focused blog post, I wanted
to offer something special to my paid subscribers as a thank-you for
your ongoing support. So, I've started writing a new book on how
reasoning works in LLMs, and here I'm sharing the first Chapter 1 with
you. This ~15-page chapter is an introduction reasoning in the context
of LLMs and provides an overview of methods like inference-time scaling
and reinforcement learning. Thanks for your support! I hope you enjoy
the chapter, and stay tuned for my next blog post on reasoning research!

</div>

</div>
