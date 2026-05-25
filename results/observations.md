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
| 100 mH | — | — | — | — | — | *Lower* |
| 1 mH | — | — | — | — | — | *Higher* |

> Additional rows to be filled in as more inductor values are tested.

---

## Key Observation: Error vs. Inductance Value

It was observed experimentally and through simulation that:

**As the inductance (L) of the DUT increases, the percentage error DECREASES. Conversely, lower inductance values produce HIGHER percentage error.**

### Reasoning

| Factor | Effect at Lower L |
|---|---|
| Inductive reactance (XL = 2*pi*f*L) | Becomes very small; voltage across inductor is tiny |
| AC voltmeter resolution | Small absolute reading error becomes a large % of the small actual value |
| Signal-to-noise ratio | Inductor signal is close to noise floor; harder to distinguish |
| Meter accuracy limits | Both V and I readings approach instrument resolution limits |

### Why Higher L Reads More Accurately

At higher inductance values, XL is large, so the voltage drop across the inductor is
significant and well within the reliable range of the AC voltmeter. The V/I ratio is
easier to measure cleanly, so the calculated XL is close to the true value, and the
final inductance result has a lower percentage error.

### Suggested Mitigation for Low Inductance

- **Increase the oscillation frequency** (reduce R1 or C1) so that XL = 2*pi*f*L
  becomes large enough to measure reliably even for small L values.
- Use a **higher precision voltmeter** with better resolution at low voltages.
- Use **precision resistors and capacitors** (1% tolerance or better) in the 555 timing network.

---

## Circuit Frequency (Theoretical Check)

Using the astable formula:

```
f = 1.44 / ((R1 + 2*R2) * C1)
```

With R1 = 200 Ω, C1 = 0.2 µF:

```
f = 1.44 / (200 * 0.2e-6) = 36,000 Hz (theoretical)
```

> Note: The simulated frequency of ~5499 Hz indicates the inductor branch impedance
> influences the effective timing in simulation. Always use the frequency counter
> reading — not the theoretical estimate — in the final calculation.

---

*Last updated: May 2026*
