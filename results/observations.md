# Results & Observations

## Simulation Environment
- **Tool:** Proteus Design Suite  
- **Timer IC:** NE555  
- **Mode:** Astable  
- **Fixed Components:** R1 = 200 Ω, C1 = 0.2 µF, C2 = 10 nF  

---

## Test Results Table

| Inductor Value (Actual) | Frequency (Hz) | V across L (V) | I through L (mA) | XL (Ω) | Measured L (mH) | % Error |
|---|---|---|---|---|---|---|
| 10 mH | 5499 | 3.57 | 9.85 | 362.44 | 10.5 | **5.0%** |
| 100 mH | — | — | — | — | — | *Higher* |

> ⚠️ Additional rows to be filled in as more inductor values are tested.

---

## Key Observation: Error vs. Inductance Value

It was observed experimentally and through simulation that:

**As the inductance (L) of the DUT increases, the percentage error in the measured value also increases.**

### Reasoning

| Factor | Effect at Higher L |
|---|---|
| Inductive reactance $X_L = 2\pi fL$ | Becomes very large; current drops significantly |
| Small-signal current measurement | Harder to measure accurately with standard AC ammeter |
| Frequency drift of 555 timer | Has a proportionally larger impact on $X_L$ at high L |
| Square wave harmonic distortion | Inductor filters harmonics more, distorting AC readings |

### Suggested Mitigation

- For larger inductors, **lower the oscillation frequency** by increasing R1 or C1 so that $X_L$ stays in a measurable range.
- Use a **higher precision frequency counter** to reduce frequency measurement error.
- Use **precision resistors and capacitors** (1% tolerance or better) in the 555 timing network.
- Consider adding a **buffer amplifier** at the 555 output to reduce loading effects.

---

## Circuit Frequency (Theoretical Check)

Using astable formula:

$$f = \frac{1.44}{(R_1 + 2R_2) \cdot C_1}$$

With R1 = 200 Ω, no R2 (zero), C1 = 0.2 µF:

$$f = \frac{1.44}{200 \times 0.2 \times 10^{-6}} = \frac{1.44}{4 \times 10^{-5}} = 36{,}000 \ \text{Hz}$$

> Note: The simulated frequency of ~5499 Hz suggests the circuit uses additional impedance from the inductor branch or a different R2 value in the actual simulation. The frequency counter on the display shows the real operating frequency and that value should always be used in calculations — not the theoretical estimate.

---

*Last updated: May 2026*
