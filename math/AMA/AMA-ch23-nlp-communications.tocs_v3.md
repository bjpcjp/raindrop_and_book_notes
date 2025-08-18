![AMA-ch23-nlp-communications](AMA-ch23-nlp-communications.best.png)

- **Natural Language for Communication**
  - Communication is the intentional exchange of information through shared signs.
  - Humans use natural language extensively, and computer agents must learn it to communicate.
  - The chapter introduces phrase structure grammars, semantics, machine translation, and speech recognition.

- **Phrase Structure Grammars**
  - N-gram models face data sparsity issues, addressed via generalization using lexical categories.
  - Chomsky’s hierarchy classifies grammars by generative capacity from recursively enumerable to regular grammars.
  - Probabilistic context-free grammars (PCFGs) assign probabilities to sentence structures to model language use.
  - The E0 grammar models a simple English fragment, with categories like noun phrases, verb phrases, and prepositional phrases.
  - Overgeneration produces ungrammatical sentences; undergeneration rejects some grammatical ones.

- **Syntactic Analysis (Parsing)**
  - Parsing recovers phrase structure from word sequences using top-down or bottom-up methods.
  - Dynamic programming techniques like chart parsing store partial results to avoid redundant work.
  - The CYK algorithm parses context-free grammars in Chomsky Normal Form efficiently in O(n³) time.
  - Ambiguity leads to exponentially many parses; CYK computes the most probable parse without enumerating all.
  - A* search with heuristics enables efficient parsing without exhaustive search.
  - Treebanks like the Penn Treebank provide parsed corpora for supervised grammar learning.
  - The inside–outside algorithm uses EM to learn PCFGs from unparsed text but faces computational challenges.
  - Lexicalized PCFGs combine phrase structure with lexical dependencies to capture word relationships.
  - PCFGs tend to favor shorter sentences; combining them with Markov models addresses this limitation.
  - Further reading: [Penn Treebank](https://catalog.ldc.upenn.edu/LDC99T42)

- **Augmented Grammars and Semantic Interpretation**
  - Augmented grammars extend PCFGs by adding attributes like case agreement, number, and head words.
  - Definite Clause Grammars (DCGs) represent grammar rules as logical clauses, enabling parsing as logical inference.
  - Case and subject–verb agreement reduce overgeneration by enforcing grammatical constraints.
  - Lexicalized PCFGs encode relations between head words, improving semantic accuracy.
  - Semantic interpretation follows compositional semantics, associating logical forms with parse trees.
  - Augmentations handle time, tense, quantification, pragmatics, speech acts, long-distance dependencies, and ambiguity.
  - Metonymy and metaphor introduce semantic complexities beyond literal meanings, requiring special modeling.
  - Disambiguation combines world knowledge, speaker intent, language models, and acoustic models.
  - Further reading: [Definite Clause Grammar](https://en.wikipedia.org/wiki/Definite_clause_grammar)

- **Machine Translation**
  - Machine translation converts text from one language to another, using models from rule-based to statistical.
  - Full interlingua approaches require deep semantic analysis and generation, which is difficult to realize practically.
  - Transfer-based systems translate at lexical, syntactic, or semantic levels via translation rules and examples.
  - Statistical machine translation learns translation and language models from bilingual corpora without handcrafted rules.
  - The noisy channel model breaks translation into source segmentation, phrase translation, and distortion (reordering).
  - Distortion models capture phrase reordering using simple distributions over position changes.
  - Large parallel corpora like Hansards and EU documents support training translation models.
  - EM algorithms iteratively improve phrase translations and distortion probabilities.
  - Further reading: [Statistical Machine Translation (Koehn, 2009)](https://www.statmt.org/book/)

- **Speech Recognition**
  - Speech recognition identifies word sequences from acoustic signals using probabilistic models.
  - The noisy channel model decomposes recognition into acoustic models and language models.
  - Acoustic signals are sampled and converted to short overlapping frames summarized by Mel-frequency cepstral coefficients (MFCCs).
  - Hidden Markov Models (HMMs) model phones as multi-state units with probabilistic transitions and emissions.
  - Pronunciation models link phones into word pronunciations, capturing dialect and coarticulation variations.
  - Language models constrain likely word sequences, often trained on task-specific corpora.
  - Speaker-dependent models achieve higher accuracy but require extensive training.
  - Accuracy depends on audio quality, vocabulary size, and application-specific constraints.
  - Further reading: [Speech and Language Processing by Jurafsky and Martin](https://web.stanford.edu/~jurafsky/slp3/)

- **Summary**
  - PCFGs balance simplicity and expressiveness but require augmentation for real language phenomena.
  - Parsing algorithms efficiently handle ambiguity by dynamic programming and heuristic search.
  - Semantic interpretation and pragmatics are crucial for meaningful understanding and disambiguation.
  - Statistical models dominate machine translation and speech recognition due to their data-driven effectiveness.
  - Large corpora are essential for training robust language, translation, and acoustic models.


