---
title: "NAND_Flash_intro — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [NAND_Flash_intro]
---

- **Address Latch Enable (ALE)** — Control signal that latches address data into the NAND device on the write signal’s rising edge.  
- **Block** — The smallest erasable unit in NAND flash, typically 128 KB consisting of multiple pages.  
- **Bad Block** — A block marked as unreliable or defective, excluded from use by system software.  
- **Byte** — The smallest programmable unit in NAND flash memory.  
- **Cache Register** — A register used to temporarily hold data during read and program operations, enabling pipelining.  
- **Chip Enable (CE#)** — Control signal that activates or deactivates the NAND device; device remains standby if not asserted.  
- **Command Latch Enable (CLE)** — Control signal that latches command cycles into the NAND device on the write signal’s rising edge.  
- **Data Register** — Register that stores data during transfer between NAND array and interface.  
- **ECC (Error-Correcting Code)** — Extra data used to detect and correct errors in stored NAND flash data for integrity.  
- **Erase Operation** — Process that resets all bits in a block to “1”; required before programming can occur.  
- **Floating-Gate Transistor (FGT)** — A transistor structure used in NAND cells to store charge and retain data without power.  
- **Multi-Level Cell (MLC)** — Flash memory cell storing multiple bits per cell, offering higher density but lower performance than SLC.  
- **NAND Flash Memory** — Non-volatile storage technology storing data in blocks with fast program/erase cycles but slower random access.  
- **Page** — The smallest unit of data read/write in NAND flash, typically 2048 bytes plus spare area for metadata.  
- **Program Operation** — Writing data to NAND flash by changing bits from “1” to “0” after erasure.  
- **Random Data Input** — Command allowing writing data to arbitrary positions within a page before final programming.  
- **Read Enable (RE#)** — Control signal that enables output data buffers to read data from NAND.  
- **Read ID Operation** — Command sequence to read manufacturer and device identification data.  
- **Read Status Operation** — Command that returns the status of the NAND device, including pass/fail and readiness.  
- **Ready/Busy (R/B#)** — Signal indicating if NAND is busy (low) or ready (high) for operations.  
- **Sector** — Subdivision of a NAND page, often 512 bytes, commonly used as a logical storage unit.  
- **Shadowing** — Technique where data is copied to RAM to allow concurrent read/write, compensating for NAND’s lack of simultaneous operations.  
- **Single-Level Cell (SLC)** — Flash memory cell storing one bit per cell with better speed and endurance than MLC.  
- **Spare Area** — Extra bytes in a NAND page used for ECC, wear-leveling, and metadata storage.  
- **TSOP-1 Package** — Common packaging format for NAND devices, supporting multiple die stacking for higher capacities.  
- **Write Enable (WE#)** — Control signal used to clock data, addresses, or commands into NAND during write operations.
