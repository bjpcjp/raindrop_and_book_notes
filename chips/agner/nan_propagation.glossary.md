- **errno** — A global or thread-safe macro variable containing an error code indicating the type of the last error, including floating point errors, but provides limited and nonspecific information.

- **fault trapping** — A hardware-supported feature that raises exceptions (traps) on numerical errors like overflow or division by zero, enabling error detection through interrupts but often slowing program execution and complicating optimization.

- **floating point number** — A computer representation of real numbers including special values like infinity (INF) and not-a-number (NAN), used in numerical calculations.

- **INF (infinity)** — A floating point special value representing overflow or division by zero with same sign operands; sign bit indicates positive or negative infinity.

- **NAN (not-a-number)** — A floating point special value representing invalid or undefined results such as 0/0 or INF-INF; includes quiet NANs and signaling NANs distinguished by mantissa bits.

- **NAN payload** — Additional bits within a quiet NAN that can store diagnostic or error information and propagate through calculations, although propagation rules lack full standardization.

- **NAN boxing** — A technique using NAN payload bits to store non-numeric data (e.g., pointers or strings) in weakly typed programming languages.

- **quiet NAN** — A type of NAN with the most significant mantissa bit set to 1, which propagates through calculations without raising traps.

- **signaling NAN** — A NAN with the most significant mantissa bit cleared and other mantissa bits set, designed to raise traps when used.

- **SIMD (Single Instruction Multiple Data)** — A parallel computing technique using vector registers and instructions to perform the same operation on multiple data elements simultaneously.

- **vectorization** — The process by which compilers convert scalar operations to SIMD instructions to improve performance, which can complicate fault trapping behavior.

- **x87 FPU Control Word** — A register controlling floating point exception behavior for the old x87 floating point unit instructions on x86 processors.

- **MXCSR register** — A control and status register managing floating point exception masks and modes for SSE and AVX instructions on x86 processors.

- **min and max functions** — Functions that return the minimum or maximum of two inputs; implementations often differ in handling NAN inputs, potentially failing to propagate NAN correctly.

- **pow function** — A function computing powers, which may fail to propagate NAN in special cases such as pow(NAN, 0) or pow(1, NAN); variations like powr and pown address these behaviors.

- **compare operations involving NAN** — Comparisons with NAN inputs always evaluate as false except for '!=' which returns true; this behavior requires careful handling of branches.

- **underflow** — A floating point condition where the result is smaller than the minimum representable positive number, resulting in zero.

- **overflow** — A floating point condition where a calculation results exceed the maximum representable value, yielding INF or -INF.

- **fused multiply-and-add (FMA)** — A floating point operation combining multiplication and addition in one step, improving performance and precision.

- **-ffinite-math-only** — A compiler option assuming no INF or NAN values occur, enabling certain optimizations but potentially breaking error detection and propagation.

- **-fno-trapping-math** — A compiler option disabling fault trapping so that operations producing NAN do not raise traps, facilitating vectorization.

- **out-of-order execution** — A CPU execution model that allows instructions to be processed non-sequentially for performance gains but complicates fault trapping and exception handling.

- **payload propagation** — The process by which NAN payload information is preserved through floating point operations, though its behavior is not fully standardized.

- **signal vs quiet compare instructions** — Compare instructions that either raise traps on NAN inputs (signaling) or treat NAN comparisons as unordered without trapping (quiet).

- **multiprecision conversion of NAN payload** — Converting NAN payloads between precisions (e.g., float to double) preserves the most significant bits, causing shifts in payload data.

- **errno reliance on fault trapping** — Using errno for floating point error detection largely depends on fault trapping, inheriting its disadvantages and overhead.
