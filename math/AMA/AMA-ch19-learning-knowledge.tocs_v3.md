![AMA-ch19-learning-knowledge](AMA-ch19-learning-knowledge.best.png)

- **Knowledge in Learning**
  - **19.1 A Logical Formulation of Learning**
    - Learning is formulated as finding logical hypotheses consistent with example descriptions and classifications.
    - Hypotheses can be generalized or specialized based on consistency with new examples, using the current-best-hypothesis search.
    - The version space algorithm maintains sets of all hypotheses consistent with examples, using boundary sets for compact representation.
    - Version space learning guarantees consistency with all seen examples and narrows down candidate hypotheses incrementally.
    - Practical challenges include noise sensitivity and exponential growth of boundary sets; limited disjunction or generalization hierarchies can mitigate this.
    - For foundational theory and algorithmic examples, see Mitchell’s work on version space learning.

  - **19.2 Knowledge in Learning**
    - Inductive learning requires hypotheses satisfying entailment constraints involving hypothesis, descriptions, and classifications.
    - Prior knowledge modifies learning from pure induction to cumulative development by incorporating background knowledge.
    - Explanation-based learning (EBL) derives general rules explained fully by background knowledge.
    - Relevance-based learning (RBL) uses prior knowledge of feature relevance to generate hypotheses consistent with observations and background.
    - Knowledge-based inductive learning (KBIL) integrates background knowledge to find hypotheses explaining observations.
    - See [Explanation-Based Learning](https://en.wikipedia.org/wiki/Explanation-based_learning) for foundational understanding.

  - **19.3 Explanation-Based Learning**
    - EBL constructs explanations from examples using background knowledge and generalizes these to create reusable rules.
    - The learning process involves proving examples, generalizing proofs by variabilization, and removing unnecessary conditions for efficiency.
    - Rule generation in EBL requires balancing operationality (ease of solving subgoals) and generality to optimize efficiency.
    - Empirical analysis guides the addition of useful rules that improve average-case complexity for expected problem distributions.
    - Key references include Mitchell et al. (1986) and Hirsh (1987) for algorithmic foundations.

  - **19.4 Learning Using Relevance Information**
    - Functional dependencies or determinations express full determination of a target attribute by relevant attributes.
    - Determinations reduce hypothesis space size by restricting learning to relevant attributes, lowering required training examples exponentially.
    - Learning minimal consistent determinations from examples uses subset search algorithms, despite NP-completeness.
    - Relevance-based decision tree learning (RBDTL) identifies relevant attributes before tree construction, improving learning efficiency over traditional methods.
    - Research on declarative bias addresses extensions for noise, continuous variables, and first-order theories; see Almuallim and Dietterich (1991).

  - **19.5 Inductive Logic Programming**
    - ILP integrates inductive learning with first-order logic representations to learn relational hypotheses expressed as logic programs.
    - Example domains include family relationships and protein folding, where relational structures cannot be captured by attributes alone.
    - Top-down ILP (e.g., FOIL) specializes general Horn clauses by adding literals until consistent with positive and negative examples.
    - Bottom-up ILP uses inverse resolution, inverting deductive proofs to generate hypotheses consistent with background knowledge and examples.
    - ILP naturally supports predicate invention, allowing concise theories and cumulative learning improvements.
    - Applications span biology, natural language processing, and scientific discovery; see Muggleton (1995) and Quinlan (1990) for foundational systems.

  - **19.6 Summary**
    - Prior knowledge enables cumulative learning by reducing hypothesis space and compactly explaining observations.
    - Different logical entailment constraints define learning techniques: EBL (deductive generalization), RBL (relevance constraints), and KBIL (background-aided induction).
    - ILP methods extend learning to first-order logic with relational hypotheses and handle predicate invention.
    - Top-down and inverse resolution approaches provide complementary ILP strategies.
    - ILP shows promise for scientific theory formation and interpretable knowledge discovery; further research focuses on efficiency and expressiveness.

- **Bibliographical and Historical Notes**
  - Prior knowledge’s role in induction was highlighted by Goodman (1954), emphasizing relevance beyond pure induction.
  - Current-best-hypothesis methods trace back to Mill (1843), with advances by Winston (1970) and Mitchell’s version space algorithms.
  - EBL evolved from planning and cognitive architectures (STRIPS, ACT*, Soar), formalized by Mitchell et al. (1986), Hirsh (1987), and others.
  - Declarative bias and functional dependencies stem from database theory and were adapted for inductive learning by Russell and Grosof (1987).
  - ILP foundations were laid by Plotkin (1971), Shapiro (1981), Quinlan (1990 FOIL), and Muggleton (1995 PROGOL), combining logic program induction and inverse resolution.
  - ILP’s predicate invention capabilities catalyze scientific discoveries, with notable successes in molecular biology and natural language processing.
  - For detailed history and key references, see Muggleton (1992), Lavrauc and Duzeroski (1994), and Page and Srinivasan (2002).

- **Exercises**
  - Exercise 19.1 proves logical entailment of relevance-based generalizations using resolution.
  - Exercises 19.2 and 19.3 analyze determinations and probabilistic extensions.
  - Exercises 19.4 and 19.5 focus on inverse resolution steps and programmatic implications for ILP.
  - Exercise 19.6 quantifies literal generation in FOIL and explores search space complexity.
  - Exercise 19.7 applies FOIL on family tree data to learn relational predicates.
  - For practice on ILP and entailment, consult [Inductive Logic Programming Exercises](https://ilp.lri.fr/exercises.html).
