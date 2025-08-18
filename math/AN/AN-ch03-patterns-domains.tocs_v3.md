![AN-ch03-patterns-domains](AN-ch03-patterns-domains.best.png)

- **Patterns and Domains**
  - **Patterns: A Communication Language**
    - Patterns originated from Christopher Alexander's architectural design theory applied to software by Kent Beck and Ward Cunningham.
    - Design patterns are proven solutions adapted to general problem classes rather than simple templates.
    - The "Gang of Four" book popularized design patterns, accelerating their research and applications in software.
    - Patterns facilitate precise, concise communication of software designs among developers.
    - See [Design Patterns: Elements of Reusable Object-Oriented Software](https://en.wikipedia.org/wiki/Design_Patterns).
  
  - **The Form of an Algorithm Pattern**
    - Algorithms are presented using fixed sections: Name, Synopsis, Context, Forces, Solution, Consequences, Analysis, and Related Algorithms.
    - This standardized pattern format enhances comparison and communication of different algorithms.
    - The format supports omission or addition of sections as needed without losing clarity.
    
  - **Pseudocode Pattern Format**
    - Algorithms precede real code with pseudocode examples for accessibility across programming language proficiencies.
    - Fact sheets summarize algorithm performance for best, average, and worst cases alongside conceptual glyphs.
    - Pseudocode uses lowercase variables, capitalized arrays with indexing, and numbered statements indicating conditional/loop scope.
    - Visualization of algorithm behavior is shown stepwise to represent execution over time.
    
  - **Design Format**
    - UML class diagrams illustrate inheritance and polymorphism relevant to Java or C++ algorithm implementations.
    - Class diagrams use symbols for visibility: # (protected), ~ (package-private), - (private), + (public).
    - Interfaces are depicted by dashed lines ending with open triangles showing implementation relationships.
  
  - **Empirical Evaluation Format**
    - Algorithm performance is benchmarked on diverse platforms ranging from desktops to high-end clusters.
    - Multiple trials per test case are averaged after discarding outliers to compute mean and standard deviation.
    - Problem sizes typically vary from small instances (n=2) up to very large instances (n=2^20).
  
  - **Domains and Algorithms**
    - Algorithm domains are generalized problem areas orthogonal to application domains, aiding appropriate algorithm selection.
    - Mapping application domains to algorithm domains remains an active research area enhancing software reuse.
    - Domain vocabularies help design reusable components and domain-specific languages (DSLs).
    - Practitioners develop informal categorizations ("war stories") to guide algorithm appropriateness.
    - Refer to [The Algorithm Design Manual](https://www.springer.com/gp/book/9780387948607) for further insights.
  
  - **Floating-Point Computations**
    - Floating-point numbers use finite bit-length representation with sign, exponent, and mantissa fields following IEEE 754.
    - Representations approximate real numbers, introducing rounding errors and relative errors commonly under one part per million.
    - Exact equality comparison of floating-point values is unreliable due to rounding; approximate equality uses tolerance values but may break transitivity.
    - IEEE 754 defines special quantities: positive/negative infinity, NaN, positive/negative zero to handle exceptional computations.
    - Performance of floating-point operations varies substantially between platforms and differs from integer operations.
    - Recommended reading: [What Every Computer Scientist Should Know About Floating-Point Arithmetic](http://docs.sun.com/source/806-3568/ncg_goldberg.html).
  
  - **Manual Memory Allocation**
    - Local variables reside on the execution stack, which grows downward in memory, while dynamic memory allocates on the heap growing upward.
    - Improper memory management can cause stack overflow (e.g., infinite recursion) or heap exhaustion (memory leaks).
    - Programmers must explicitly free dynamically allocated memory to prevent leaks.
    - Examples demonstrate stack growth in recursion and heap exhaustion through uncontrolled allocations.
    - Understanding addresses and stack-heap interaction is critical for memory-safe programming.
  
  - **Choosing a Programming Language**
    - Selecting a programming language depends on factors including garbage collection support versus manual memory management.
    - Bytecode interpreted languages (e.g., Java) offer portability but may trade off runtime performance compared to compiled languages.
    - Static typing enables early error detection at compile time; dynamic typing offers flexibility with runtime checks.
    - Optimization strategies and language choice influence implementation efficiency but are beyond this book's scope.
