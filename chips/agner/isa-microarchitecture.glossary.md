- **AGI stall** — Delay caused when an instruction's memory address depends on the result of the immediately preceding instruction, forcing an extra clock cycle before address calculation.

- **Branch history register** — A register storing the outcomes (taken/not taken) of the last n branches for use in branch prediction.

- **Branch indicator** — Bits associated with code blocks indicating the presence and type of branches for prediction purposes.

- **Branch target buffer (BTB)** — A cache storing the target addresses of branch instructions to predict where branches will go before execution.

- **Call instruction** — A control transfer instruction that invokes a subroutine and saves the return address on the stack or in a return stack buffer.

- **Close jumps** — Branch instructions located so close in memory that their branch target buffer entries overlap or conflict, causing mispredictions.

- **Double-sized µop** — A micro-operation that requires two trace cache entries due to large immediate operands or complex addressing.

- **Dynamic prediction** — Branch prediction that adapts based on runtime history and patterns rather than fixed static heuristics.

- **Entry replacement** — The process of a new BTB entry displacing an existing one, often due to set associativity limits.

- **Execution unit** — The hardware component that performs arithmetic, logical, or other instructions in a CPU pipeline.

- **Fall through** — The case when a conditional branch is not taken and instruction execution continues sequentially.

- **Floating point stack engine** — A mechanism managing the register stack and renaming of floating point registers for parallel execution.

- **Hybrid predictor** — A branch predictor combining two or more methods, such as loop counters and two-level adaptive predictors, using a meta-predictor.

- **Instruction pipeline** — The sequence of stages an instruction passes through in a CPU, such as fetch, decode, execute, and retire.

- **Loop counter predictor** — A specialized branch predictor targeting loop branches that tracks loop iteration counts to predict loop exits.

- **Misprediction penalty** — The number of wasted clock cycles incurred when the CPU speculatively executes the wrong branch path.

- **Micro-operation (µop)** — A simplified internal operation derived from one complex instruction, enabling out-of-order execution.

- **Out-of-order execution** — CPU technique allowing instructions to be processed as soon as operands are available, not necessarily in program order.

- **Pattern history table** — A table indexed by branch history used to store saturating counters for predicting branch directions.

- **Perceptron predictor** — A branch prediction method using weighted sums mimicking a neural network to learn complex branch patterns.

- **Prefixed instruction** — An instruction preceded by one or more prefix bytes that can affect its execution characteristics and pipeline behavior.

- **Previous branch aliasing** — Interference caused when multiple branches share entries or indexes in a branch prediction structure.

- **Register renaming** — Technique of mapping logical registers to physical registers dynamically to avoid false dependencies.

- **Return stack buffer (RSB)** — A hardware stack storing return addresses of subroutine calls to predict return targets efficiently.

- **Saturating counter** — A small state machine used in branch prediction to track how often a branch is taken or not.

- **Static branch prediction** — A fixed prediction made before runtime, often based on branch direction (forward or backward).

- **Trace cache** — A cache storing decoded micro-operations or sequences of operations (traces) to speed up instruction dispatch.

- **Two-level adaptive predictor** — A branch predictor using a branch’s local or global history to select a prediction from per-pattern counters.

- **µop fusion** — The combination of multiple micro-operations into a single micro-op for optimized execution (mentioned indirectly).

- **µop queue** — A buffer holding decoded micro-operations before they enter the execution pipeline (mentioned indirectly).
