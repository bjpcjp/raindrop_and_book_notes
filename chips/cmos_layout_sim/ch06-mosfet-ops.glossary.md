- **Accumulation** — MOSFET operation region when VGS < 0, causing mobile holes to accumulate under the gate oxide, resulting in capacitance predominantly between the gate and bulk through a parasitic resistance.

- **Body Effect** — Increase in MOSFET threshold voltage that occurs when the source voltage is higher than the substrate voltage, requiring a larger gate voltage to invert the channel.

- **Body Factor (γ)** — Parameter representing the effect of source-to-substrate voltage on threshold voltage, proportional to the square root of substrate doping divided by oxide capacitance.

- **Capacitance (MOSFET)** — Includes gate-to-bulk capacitance (Cgb), gate-to-source/drain overlap capacitances (Cgs, Cgd), and varies depending on device operation region (accumulation, depletion, strong inversion).

- **Channel Length Modulation (CLM)** — Effect in the saturation region where the effective channel length reduces with increased VDS, causing the drain current to increase slightly beyond saturation.

- **Depletion (Weak Inversion)** — MOSFET region where the surface under the gate is depleted of free carriers but not yet inverted, resulting in oxide capacitance in series with a depletion capacitance.

- **Drain-Induced Barrier Lowering (DIBL)** — Short-channel effect where increased drain voltage lowers the device threshold voltage by attracting electrons under the gate oxide near the drain.

- **Drift Current** — Carrier transport mechanism in strong inversion where the electric field moves carriers from source to drain.

- **Flatband Voltage (V_FB)** — Voltage at which the surface potential equals the bulk potential, indicating no band bending at the oxide-semiconductor interface.

- **Gate-Induced Drain Leakage (GIDL)** — Leakage current component caused by minority carriers swept into the substrate under high drain voltage when the device is in accumulation.

- **Hot Carriers** — High-energy carriers near the drain of a short-channel MOSFET that can cause gate oxide damage and threshold voltage shifts.

- **Lateral Diffusion (L_diff)** — Extension of source/drain regions into the channel, affecting the effective channel length of a MOSFET.

- **Lightly-Doped Drain (LDD)** — Implant structure used to reduce electric field peaks near the drain by adding a lightly doped region between channel and heavily doped source/drain.

- **Mobility (μ)** — Ratio of carrier velocity to electric field; decreases above a critical electric field due to velocity saturation.

- **On-Current (I_on or I_drive)** — The maximum drain current of a MOSFET with gate and drain at VDD, important for determining transistor strength.

- **Oxide Capacitance (C_ox)** — Capacitance per unit area of the gate oxide layer, defined by dielectric constant and oxide thickness.

- **Punchthrough** — Condition where depletion regions extend across the entire channel length, causing large current leakage and device failure.

- **Short-Channel Effects** — Unwanted phenomena in scaled MOSFETs including threshold voltage roll-off, DIBL, velocity saturation, and hot-carrier effects.

- **Source-to-Bulk Voltage (V_SB)** — Potential difference between source and substrate that influences threshold voltage via the body effect.

- **SPICE MOSFET Models** — Circuit simulation models (levels 1,2,3, BSIM) capturing device characteristics including threshold voltage, mobility degradation, and capacitances.

- **Subthreshold Current** — Drain current that flows when VGS is below threshold voltage, dominated by diffusion rather than drift, with an exponential relation to VGS.

- **Subthreshold Slope** — Voltage change needed to change drain current by one decade in the subthreshold region, ideally ~60 mV/decade at room temperature.

- **Surface States / Interface Trapped Charges (Q_ss)** — Charges present at the oxide-semiconductor interface that affect threshold voltage and device behavior.

- **Threshold Voltage (V_TH)** — Gate voltage at which a strong inversion channel forms, enabling significant conduction between source and drain.

- **Triode Region** — MOSFET operating region where V_DS < V_GS - V_TH and the channel extends from source to drain, behaving like a voltage-controlled resistor.

- **Velocity Saturation** — Phenomenon where carrier velocity saturates at high electric fields, limiting the increase of drain current in short-channel devices.

- **Well (Bulk) Connection** — Substrate region tied to a fixed voltage (e.g., ground or VDD), affecting device capacitances and threshold voltage.
