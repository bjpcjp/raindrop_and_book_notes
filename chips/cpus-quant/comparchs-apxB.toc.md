```markdown
# Table of Contents

- B Review of Memory Hierarchy  
  - B.1 Introduction .............................................. B-2  
    - Cache Basics  
    - Memory Hierarchy Levels (Figure B.1)  
    - Cache Performance Review  
    - Example: Cache Miss Impact on CPI  
    - Four Memory Hierarchy Questions  
      - Q1: Where Can a Block Be Placed in a Cache?  
      - Q2: How Is a Block Found If It Is in the Cache?  
      - Q3: Which Block Should Be Replaced on a Cache Miss?  
      - Q4: What Happens on a Write?  
    - Example: The Opteron Data Cache  
    - Instruction vs. Data Caches (Figure B.6)  

  - B.2 Cache Performance ...................................... B-16  
    - Average Memory Access Time  
    - Examples Calculating Cache Performance and CPI  
    - Miss Penalty and Out-of-Order Execution Processors  
    - Summary Performance Equations (Figure B.7)  

  - B.3 Six Basic Cache Optimizations .................... B-23  
    - Three Categories of Cache Misses (Three C's)  
      - Compulsory  
      - Capacity  
      - Conflict  
    - First Optimization: Larger Block Size to Reduce Miss Rate  
      - Examples and Trade-offs (Figures B.10, B.11, B.12)  
    - Second Optimization: Larger Caches to Reduce Miss Rate  
    - Third Optimization: Higher Associativity to Reduce Miss Rate  
      - Example with Hit Time Trade-offs (Figure B.13)  
    - Fourth Optimization: Multilevel Caches to Reduce Miss Penalty  
      - Local vs. Global Miss Rate  
      - Examples and Figures (B.14, B.15)  
    - Fifth Optimization: Giving Priority to Read Misses Over Writes  
    - Sixth Optimization: Avoiding Address Translation During Cache Indexing  
      - Virtual vs. Physical Caches  
      - Page Coloring and Synonyms  
      - Example Cache Indexing with TLBs (Figure B.17)  
    - Summary of Cache Optimizations (Figure B.18)  

  - B.4 Virtual Memory ........................................... B-40  
    - Historical Context and Overview  
    - Comparison of Parameters (Figure B.20)  
    - Paging vs. Segmentation (Figures B.21, B.22)  
    - Revisiting the Four Memory Hierarchy Questions for Virtual Memory  
      - Q1: Block Placement  
      - Q2: Block Identification (Page Table, Inverted Page Table)  
      - Q3: Replacement Policy (LRU, Use Bits)  
      - Q4: Write Strategy (Write-Back)  
    - Techniques for Fast Address Translation (TLBs)  
      - Example Opteron TLB (Figure B.24)  
    - Selecting Page Size: Trade-offs and Multiple Page Sizes  

  - B.5 Protection and Examples of Virtual Memory ..... B-49  
    - Multiprogramming and Process Protection Overview  
    - Protection Rings and Capability-Based Systems  
    - Intel 80x86 Protection Models: Segmented and Flat Address Spaces  
    - Summary of Address Translation and Cache Interaction (Figure B.25)  
```
