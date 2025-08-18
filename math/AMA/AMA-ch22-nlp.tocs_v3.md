![AMA-ch22-nlp](AMA-ch22-nlp.best.png)

- **Natural Language Processing**
  - **Language Models**
    - N-gram models predict probability distributions of language expressions using Markov chain assumptions.
    - Character n-gram models can identify languages, correct spelling, classify genre, and recognize named entities.
    - Smoothing techniques, such as backoff and linear interpolation, adjust probabilities of low-frequency sequences.
    - Perplexity measures the quality of language models by quantifying the weighted average branching factor.
    - Word n-gram models handle large vocabularies and require mechanisms for out-of-vocabulary words like <UNK>.
    - Further reading: [Jurafsky & Martin, Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/)

  - **Text Classification**
    - Text classification assigns predefined categories to texts, exemplified by spam detection and sentiment analysis.
    - Features include word n-grams, character patterns, and metadata such as sender or time of arrival.
    - Classification algorithms include naive Bayes, SVMs, decision trees, logistic regression, and data compression methods.
    - Feature selection optimizes classifier performance by removing non-discriminative features.
    - Further reading: [Sebastiani, Machine Learning in Automated Text Categorization](https://doi.org/10.1016/S0893-6080(01)00064-3)

  - **Information Retrieval**
    - Information retrieval (IR) systems locate documents relevant to user queries with query languages and result presentations.
    - Early Boolean keyword models have been largely replaced by statistical models like BM25 that weigh term frequency, inverse document frequency, and document length.
    - BM25 relies on parameters k and b, tunable via cross-validation, to balance term frequency and document normalization.
    - Link-analysis algorithms such as PageRank and HITS improve ranking by evaluating in-links weighted recursively by quality.
    - IR evaluation uses precision, recall, and F1 score; Web-scale IR emphasizes precision at top-ranked results.
    - Further reading: [Manning, Raghavan & Schütze, Introduction to Information Retrieval](https://nlp.stanford.edu/IR-book/)

  - **Question Answering**
    - Question answering systems return concise answers rather than document lists by issuing query rewrites to search engines.
    - Systems like ASK MSR leverage the breadth of Web content and n-gram frequency scoring to extract probable answers.
    - Question focus types direct filtering of answers, such as filtering for people in "who" questions.
    - Precision emphasis is key since multiple rephrasings likely exist in large corpora.
    - Further reading: [Banko et al., Open Information Extraction from the Web](https://www.aaai.org/Papers/AAAI/2007/AAAI07-282.pdf)

  - **Information Extraction**
    - Information extraction acquires structured knowledge by identifying objects and relations within texts using models of increasing sophistication.
    - Finite-state automata and regular expressions extract attributes and relational data in constrained domains using cascaded transducers.
    - Hidden Markov models (HMMs) introduce probabilistic tolerance to noise with hidden states representing template segments.
    - Conditional Random Fields (CRFs) model conditional probability sequences discriminatively, allowing overlapping, rich features and higher accuracy.
    - Ontology extraction employs high-precision, general templates to infer hierarchical relations from large corpora.
    - Automated template construction builds extraction patterns iteratively from small seed examples expanding coverage.
    - Machine reading systems like TEXTRUNNER use taxonomies of general templates and linear-chain CRFs to extract relations domain-independently from vast Web corpora.
    - Further reading: [Lafferty, McCallum & Pereira, Conditional Random Fields: Probabilistic Models for Segmenting and Labeling Sequence Data](https://repository.upenn.edu/cgi/viewcontent.cgi?article=1162&context=cis_papers)
