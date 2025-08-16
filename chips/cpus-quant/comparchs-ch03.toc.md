```markdown
# Table of Contents

- 3 Instruction-Level Parallelism and Its Exploitation
  - 3.1 Instruction-Level Parallelism: Concepts and Challenges
    - Instruction-Level Parallelism: Concepts and Challenges . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 149
    - What Is Instruction-Level Parallelism? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 150
    - Data Dependences and Hazards . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 151
    - Data Dependences . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 151
    - Name Dependences . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .153
    - Data Hazards . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 153
    - Control Dependences . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 154
  - 3.2 Basic Compiler Techniques for Exposing ILP
    - Basic Pipeline Scheduling and Loop Unrolling . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 157
  - 3.3 Reducing Branch Costs with Advanced Branch Prediction
    - Correlating Branch Predictors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 162
    - Tournament Predictors: Adaptively Combining Local and Global Predictors . . . . . . . . . . . . . . . . . . . . . . . . . . . 164
    - The Intel Core i7 Branch Predictor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 166
  - 3.4 Overcoming Data Hazards with Dynamic Scheduling
    - Dynamic Scheduling: The Idea . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 168
    - Dynamic Scheduling Using Tomasulo’s Approach . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 170
  - 3.5 Dynamic Scheduling: Examples and the Algorithm
    - Examples of Tomasulo’s Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 176
    - Tomasulo’s Algorithm: The Details . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 179
    - Tomasulo’s Algorithm: A Loop-Based Example . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 180
  - 3.6 Hardware-Based Speculation
    - Speculation and Dynamic Scheduling . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 183
    - ROB and Instruction Execution with Speculation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 184
    - Speculative Execution: Examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 187
    - Handling Exceptions and Branch Mispredictions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 189
  - 3.7 Exploiting ILP Using Multiple Issue and Static Scheduling
    - Multiple-Issue Processor Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 192
    - The Basic VLIW Approach . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 193
```
