---
title: "SER-mechanisms-GPU-regfiles — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [SER-mechanisms-GPU-regfiles]
---

- **Architectural Vulnerability Factor (AVF)** — The fraction of time during execution when a hardware component is vulnerable to soft errors that can cause failure.  
- **Base-Delta Immediate (BDI) Compression** — A data compression method that stores values as a base plus small differences (deltas) to reduce storage size.  
- **Compression State** — Metadata indicating how a register value is compressed (e.g., AllZero, B4D0, B4D1, uncompressed).  
- **Critical Time** — The time period during which a register’s incorrect value can propagate and cause system errors.  
- **Divergent Warp** — A GPU warp in which not all threads execute the same instruction path, leading to varying active threads during execution.  
- **Double Bit Error** — An error scenario where two bits flip in a data word, often harder to detect and correct than single-bit errors.  
- **ECC (Error-Correction Code)** — A method to detect and correct errors in stored or transmitted data using additional check bits.  
- **Execution Unit (GPU)** — The processing elements in a GPU that execute instructions on threads.  
- **Hardening (Selective Hardening)** — Designing specific parts of hardware, such as register file bytes, with radiation-hardened or soft-error-immune circuitry to improve reliability.  
- **Narrow-Width Values** — Data values that require fewer bytes than their declared data type width, allowing compression by storing fewer bytes.  
- **Non-Divergent Warp** — A GPU warp where all threads execute the same instruction, enabling optimizations like warp-level compression.  
- **Register File (RF)** — A large, fast storage area in GPU cores that holds registers for executing threads.  
- **Register Vulnerability** — The susceptibility of register data to soft errors during their critical time windows.  
- **Selective Hardening Granularity** — The size of the portion of the register file entry (e.g., bytes) designed with hardened memory to reduce vulnerability.  
- **SIMT (Single Instruction Multiple Thread)** — GPU execution model where instructions are executed simultaneously by multiple threads in a warp.  
- **Soft Error (SE)** — A temporary fault in hardware caused by external events (e.g., radiation) that flips stored bits without causing permanent damage.  
- **Soft-Error Vulnerability (SEV)** — Measure of the likelihood that a soft error will cause failure in a hardware unit.  
- **STT-RAM** — Spin-Transfer Torque RAM, a non-volatile memory technology with different reliability and performance characteristics than SRAM.  
- **Thread-Level Compression (ThreadC)** — A compression method that individually compresses each thread’s register value, effective even for divergent warps.  
- **Warp-Level Compression (WarpC)** — A compression technique exploiting value similarity across all threads in a warp to reduce register file bit vulnerability.  
- **Warp Register** — An architectural register associated with a warp, collectively representing the registers of all threads in that warp.  
- **Thread Register** — The register corresponding to an individual thread within a warp.  
- **Vulnerable Bits** — Bits in hardware storage elements that are susceptible to soft errors during critical periods.
