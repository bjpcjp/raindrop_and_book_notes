- C Computational Complexity  
  - C.1 Asymptotic Notation  
    - Explanation and illustration of asymptotic notation (big-Oh) and its use in characterizing function growth and algorithm complexity.  
      Big-Oh notation provides an upper bound on the growth of functions as their input approaches a limit, commonly used to describe time or space complexity. The text details how constants and combinations of terms influence the order, emphasizing the fastest growing term as dominant. Examples show how to apply and interpret this notation. Further reading: [Introduction to Asymptotic Notation](https://en.wikipedia.org/wiki/Big_O_notation).  
  - C.2 Time Complexity Classes  
    - Overview of key time complexity classes: P, NP, NP-hard, and NP-complete, including their relationships and importance in computational theory.  
      P contains problems solvable in polynomial time; NP includes problems verifiable in polynomial time; NP-hard problems are at least as difficult as the hardest NP problems; NP-complete are both NP and NP-hard. The assumed inequality P ≠ NP underpins many cryptographic systems. The section introduces polynomial transformations and the foundational 3SAT problem. Further reading: [Complexity classes P and NP](https://en.wikipedia.org/wiki/P_complexity_class).  
  - C.3 Space Complexity Classes  
    - Description of space complexity classes, focusing on PSPACE, and its relation to time complexity classes.  
      PSPACE denotes problems solvable using polynomial memory without time constraints, distinguishing memory reuse from time's one-way progression. P and NP are subsets of PSPACE, but it is unknown if PSPACE contains problems outside NP. Polynomial-time reductions define PSPACE-hard and PSPACE-complete problems analogous to NP. Further reading: [PSPACE Complexity Class](https://en.wikipedia.org/wiki/PSPACE).  
  - C.4 Decideability  
    - Discussion of undecidable problems, highlighting the halting problem as a canonical example.  
      Undecidable problems lack guaranteed finite-time algorithms for general resolution. The halting problem demonstrates this for arbitrary programs in Turing complete languages, with no universal method able to decide termination. Some specific cases can be decided, but no algorithm exists for the general case. Further reading: [Halting Problem](https://en.wikipedia.org/wiki/Halting_problem).
