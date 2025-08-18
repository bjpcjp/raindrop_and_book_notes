[Representative image](ADM-ch18-sets-strings.best.png)

- **18.1 Set Cover**
  - The set cover problem seeks the smallest subset of given subsets whose union covers the entire universal set.
  - It is NP-complete and harder than vertex cover, with the best approximation algorithm achieving Θ(lg n) times optimal.
  - The greedy heuristic selects the largest subsets repeatedly and achieves at most ln n times the optimal size.
  - Integer linear programming formulations provide powerful exact and weighted variants.
  - See the survey [BP76] for classical results and [SDK83] for algorithmic expositions.

- **18.2 Set Packing**
  - Set packing requires selecting mutually disjoint subsets from a collection, often covering the universal set exactly once.
  - Exact cover problems are NP-complete and model applications like airline crew scheduling.
  - Greedy heuristics select subsets while avoiding conflicts, optionally augmented by randomization or exhaustive search.
  - Integer programming formulations with disjointness constraints can model and solve set packing problems.
  - The survey [BP76] and [SDK83] provide comprehensive algorithmic and application discussions.

- **18.3 String Matching**
  - String matching locates pattern occurrences in texts, widely applied in text editors, search, and bioinformatics.
  - The Knuth-Morris-Pratt algorithm preprocesses patterns to enable linear worst-case-time matching.
  - Boyer-Moore matches from right to left, often skipping large text portions, performing well on longer patterns.
  - For multiple patterns, Aho-Corasick builds finite automata for efficient simultaneous searches.
  - See [Gus97] for foundational algorithms and [AC75] for Aho-Corasick methodology.

- **18.4 Approximate String Matching**
  - Approximate matching finds minimal-cost transformations (insertions, deletions, substitutions) between strings.
  - Dynamic programming solves the edit distance problem with O(mn) time and can be optimized for similar strings or space.
  - Bit-parallel algorithms leverage computer word operations for efficiency on short patterns.
  - Gap penalties model runs of insertions/deletions and are solvable with affine-gap dynamic programming.
  - Key references include [NR07] for bit-parallel methods and [SK99] for applications in biology.

- **18.5 Text Compression**
  - Text compression encodes data into shorter strings allowing perfect reconstruction, saving storage and bandwidth.
  - Lossless methods are necessary for documents, while lossy methods apply for images and audio.
  - Huffman coding creates variable-length prefix codes based on symbol frequencies via a greedy O(n log n) algorithm.
  - Lempel-Ziv algorithms build adaptive dictionaries of substrings dynamically, achieving robust compression.
  - Recommended resources are [Say05] for recent overviews and [BCW90] for foundational content.

- **18.6 Cryptography**
  - Cryptography secures messages against unauthorized access and supports authentication and integrity.
  - Caesar ciphers shift letters but are weak; block ciphers like DES and AES shuffle bits with secret keys.
  - Public key cryptography, such as RSA, uses separate encryption and decryption keys to solve distribution problems.
  - Checksum methods (e.g., CRC) detect errors; cryptographic hashes (MD5, SHA-256) detect malicious changes.
  - The Handbook of Applied Cryptography [MOV96] provides comprehensive cryptographic background.

- **18.7 Finite State Machine Minimization**
  - Minimizing deterministic finite automata reduces states while preserving language recognition.
  - Partition-refinement algorithms iteratively split states until no further distinctions exist.
  - Conversion from nondeterministic to deterministic automata is possible but may cause exponential state growth.
  - Regular expressions can be translated to automata using epsilon transitions or derivatives methods.
  - Tools include Grail+ and FSM Library; foundational theory in [Hop71] and [Aho90].

- **18.8 Longest Common Substring/Subsequence**
  - The longest common substring is the longest consecutive character sequence common to all input strings.
  - Suffix trees identify common substrings efficiently; longest common subsequence finds scattered common characters.
  - Dynamic programming solves longest common subsequence in O(mn) time for two strings.
  - Faster algorithms use the Hunt-Szymanski technique when matches are sparse; permutations allow O(n log n) solutions.
  - Surveys [BHR00] and applications in biology are detailed in [Gus97].

- **18.9 Shortest Common Superstring**
  - The shortest common superstring is the minimal-length string containing all given strings as substrings.
  - It is NP-complete and reducible to asymmetric traveling salesman problems.
  - The greedy heuristic merges pairs of strings with maximum overlap iteratively and has approximation bounds up to 3.5.
  - Applications include DNA sequencing fragment assembly and sparse matrix compression.
  - See [MKT07] for recent surveys and [BJL+94] for approximation algorithms.
