---
title: "ch16-memory-basics — Glossary"
layout: default-foundation-20210515
date: 2025-08-13
tags: [ch16-memory-basics]
---

- **1T1C (one-transistor, one-capacitor) DRAM cell** — A memory cell consisting of one access transistor and one capacitor storing the data charge.
- **Access MOSFET** — A MOS transistor used to connect the memory cell capacitor to the bit line during read or write operations.
- **Bit line (digit line / column line)** — A vertical conductor in the memory array that carries data to or from memory cells.
- **Body effect** — A phenomenon where the threshold voltage of a MOSFET changes due to the voltage difference between the body (substrate) and source terminals.
- **Capacitance (Ccol, Cmbit, Ccoi, Cox, Ctox)** — Electrical storage of charge; in the context includes bit line capacitance, memory bit capacitance, coupling capacitance, oxide capacitance, and tunneling oxide capacitance.
- **Charge sharing** — The redistribution of charge among connected capacitors, affecting voltage levels in memory sensing.
- **Column decoder** — Circuitry used to select a specific column (bit line) in the memory array based on the column address.
- **Contention current** — Current caused by simultaneous conduction paths from VDD to ground, often during sense amplifier switching.
- **Dynamic RAM (DRAM)** — A volatile memory type that stores data as charge on capacitors and requires periodic refreshing.
- **Electrically Erasable Programmable Read-Only Memory (EEPROM)** — A memory device that can be electrically programmed and erased via tunneling mechanisms.
- **Equilibration circuitry (Eq signal)** — Circuitry used to precharge and equalize bit lines to a known voltage before a sensing operation.
- **Folded array architecture** — Memory array layout where two arrays are placed adjacent for matched noise immunity on bit lines.
- **Floating gate MOSFET** — A MOS device with a floating (isolated) gate layer that can store charge to alter the transistor threshold voltage, used in nonvolatile memories.
- **Gate-drain overlap capacitance** — Parasitic capacitance formed where the gate polysilicon overlaps the drain region of a MOSFET.
- **Hot electron injection (CHE)** — A programming mechanism where high-energy electrons are injected onto the floating gate via channel current.
- **Kickback noise** — Noise injected back into the input nodes of a sense amplifier during switching, affecting sensing accuracy.
- **Local decoder** — A decoding circuit situated near the memory array to select specific rows or columns, reducing signal routing complexity.
- **Long L MOSFET (Long channel transistor)** — A transistor with intentionally increased channel length, often used as a weak driver or resistor.
- **Memory cell** — The basic storage element of a semiconductor memory, e.g., DRAM or SRAM cell.
- **Metastability** — An unstable operating point in a sense amplifier or comparator where its output behavior is unpredictable due to minimal input difference.
- **NMOS Sense Amplifier (NSA)** — A sense amplifier using NMOS transistors, typically faster but only capable of pulling bit lines down.
- **Open array architecture** — A memory array layout where two separate arrays share a sense amplifier between their bit lines.
- **Pass transistor** — A MOS transistor used as a switch to pass signals or data in decoders and memory circuits.
- **PMOS Sense Amplifier (PSA)** — A sense amplifier using PMOS transistors, capable of driving bit lines up to full logic levels.
- **Precharge-evaluate (PE) logic** — A dynamic logic style that precharges outputs and conditionally evaluates based on inputs.
- **Refresh operation** — The periodic action in DRAMs to restore charge on storage capacitors to prevent data loss.
- **Row decoder** — Circuitry used to select a specific row (word line) in the memory array based on the row address.
- **Row (word) line** — A horizontal conductor in the memory array that controls the access transistors of a row of memory cells.
- **Sense amplifier** — Circuit that detects and amplifies the small voltage change on a bit line caused by accessing a memory cell.
- **Threshold voltage (VTHN)** — The minimum gate voltage needed to create a conducting channel in a MOSFET.
- **Word line driver (row driver)** — Circuit that drives the word (row) line to voltages greater than VDD to fully turn on access transistors.
