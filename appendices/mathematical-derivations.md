# Appendix: Mathematical Derivations

## 1. Arrhenius Temperature Dependence of Reaction Rate

### Derivation: CVD Decomposition Kinetics

The rate of chemical decomposition follows Arrhenius kinetics:

```
k(T) = A × exp(−Ea / RT)
```

Where:
- k(T) = temperature-dependent rate constant (s⁻¹)
- A = pre-exponential factor (frequency of collisions)
- Ea = activation energy (J/mol)
- R = gas constant = 8.314 J/(mol·K)
- T = absolute temperature (K)

### Physical Interpretation

At low temperature: exp term ≈ 0 → k ≈ 0 (negligible reaction)
At high temperature: exp term → 1 → k ≈ A (diffusion-limited)

### Numerical Application: WF₆ Decomposition

For WF₆ thermal decomposition:
- A ≈ 10¹² s⁻¹ (pre-exponential)
- Ea ≈ 180 kJ/mol (typical for fluorine compound decomposition)

**At 400°C (673 K):**
```
k(673) = 10¹² × exp(−180,000 / (8.314 × 673))
       = 10¹² × exp(−32.12)
       = 10¹² × 1.07 × 10⁻¹⁴
       ≈ 0.011 s⁻¹
```
**Decomposition time constant: τ = 1/k ≈ 90 seconds**

**At 500°C (773 K):**
```
k(773) = 10¹² × exp(−180,000 / (8.314 × 773))
       = 10¹² × exp(−27.98)
       = 10¹² × 7.6 × 10⁻¹³
       ≈ 0.76 s⁻¹
```
**Decomposition time constant: τ = 1/k ≈ 1.3 seconds**

**Conclusion:** Raising temperature 100°C reduces decomposition time ~70x. This sensitivity requires precise temperature control in CVD reactors.

---

## 2. Equivalent Oxide Thickness (EOT) Scaling

### Definition

```
EOT = t_hk / κ_rel
```

Where:
- EOT = SiO₂-equivalent thickness
- t_hk = physical thickness of high-κ material (nm)
- κ_rel = relative permittivity: κ_rel = κ_material / κ_SiO₂ = κ_material / 3.9

### Capacitance Relationship

Capacitance of dielectric stack:
```
C = ε₀ × εr / t
```

For SiO₂:
```
C_SiO₂ = ε₀ × 3.9 / t_SiO₂
```

For high-κ material with same capacitance:
```
C_hk = ε₀ × κ_hk / t_hk = C_SiO₂
```

Therefore:
```
κ_hk / t_hk = 3.9 / t_SiO₂
t_SiO₂ = (3.9 / κ_hk) × t_hk
EOT = t_hk × (3.9 / κ_hk) = t_hk / κ_rel
```

### Numerical Example: HfO₂ Scaling

At 3nm node: Target EOT = 0.4 nm

For HfO₂ (κ = 25):
```
κ_rel = 25 / 3.9 ≈ 6.4
t_HfO₂ = EOT × κ_rel = 0.4 × 6.4 = 2.56 nm
```

**With pure SiO₂ (κ = 3.9):**
```
t_SiO₂ = 0.4 nm (impossible; only ~1-2 atomic layers; tunneling catastrophic)
```

**Conclusion:** High-κ materials enable node scaling by achieving required capacitance with thicker films.

---

## 3. Electromigration Lifetime (Black's Equation)

### Black's Equation Derivation

Electromigration-induced void growth follows:

```
MTF (hours) = K / j^n × exp(Ea / kT)
```

Where:
- K = material constant
- j = current density (A/cm²)
- n = exponent (~2 for copper)
- Ea = activation energy (~0.7 eV for Cu)
- k = Boltzmann constant = 1.38 × 10⁻²³ J/K = 8.617 × 10⁻⁵ eV/K
- T = absolute temperature (K)

### Physical Mechanism

Current density increases copper atom drift velocity via electron wind force:
```
v_drift = Z* × e × ρ × j / m
```

Where Z* = effective charge (wind force effect).

Higher drift velocity → faster void nucleation → shorter MTTF.

### Numerical Calculation: Copper Interconnect

For copper at 400 K (operating temperature):

**Parameters:**
- K ≈ 10⁻⁶ (for copper; empirical)
- j = 10⁶ A/cm² (sub-2nm current density)
- n = 2
- Ea = 0.7 eV
- k = 8.617 × 10⁻⁵ eV/K
- T = 400 K

**Calculation:**
```
MTF = 10⁻⁶ / (10⁶)² × exp(0.7 / (8.617 × 10⁻⁵ × 400))
    = 10⁻⁶ / 10¹² × exp(0.7 / 0.0345)
    = 10⁻¹⁸ × exp(20.3)
    = 10⁻¹⁸ × 6.0 × 10⁸
    = 0.6 × 10⁻⁹ hours
```

**Result:** MTF ≈ 0.6 nanoseconds (completely unacceptable; device fails in microseconds)

**With alloyed Cu-Mn (Ea = 0.9 eV):**
```
MTF = 10⁻¹⁸ × exp(0.9 / 0.0345)
    = 10⁻¹⁸ × exp(26.1)
    = 10⁻¹⁸ × 1.7 × 10¹¹
    = 0.17 × 10⁻⁶ hours ≈ 0.6 microseconds
```

**Still unacceptable for sub-2nm; requires further architectural changes (wider lines, redundancy).**

---

## 4. Deposition Rate via Faraday's Law

### Electroplating Deposition Rate

Faraday's Law relates electrical current to mass deposited:

```
m = (M × Q) / (n × F)
```

Where:
- m = mass deposited (grams)
- M = molar mass of element (g/mol)
- Q = total charge passed (Coulombs)
- n = number of electrons transferred per ion
- F = Faraday constant = 96,485 C/mol

For continuous current:
```
Q = I × t
```

Combining:
```
m = (M × I × t) / (n × F)
```

Dividing by time to get rate:
```
dm/dt = (M × I) / (n × F)
```

Normalizing by area:
```
Deposition rate (cm/s) = (M × i) / (n × F × ρ)
```

Where:
- i = current density (A/cm²)
- ρ = material density (g/cm³)

### Numerical Application: Copper Electroplating

Parameters:
- M (Cu) = 63.5 g/mol
- n = 2 (Cu²⁺ + 2e⁻ → Cu)
- F = 96,485 C/mol
- ρ (Cu) = 8.96 g/cm³
- i = 10 mA/cm² = 0.01 A/cm²

**Rate calculation:**
```
Rate = (63.5 × 0.01) / (2 × 96,485 × 8.96)
     = 0.635 / 1.73 × 10⁶
     = 3.67 × 10⁻⁷ cm/s
     = 3.67 × 10⁻⁹ m/s
     = 0.0367 nm/s
     = 2.2 nm/min
```

**For 1 μm (1000 nm) copper deposition:**
```
Time = 1000 nm / 2.2 nm/min ≈ 450 minutes ≈ 7.5 hours per wafer
```

---

## 5. ALD Saturation Kinetics (Langmuir)

### Langmuir Adsorption Model

Fractional surface coverage as function of time:

```
θ(t) = θ_sat × [1 − exp(−t / τ)]
```

Where:
- θ(t) = fractional coverage at time t
- θ_sat = maximum coverage (1 for monolayer)
- τ = saturation time constant (seconds)
- t = exposure time (seconds)

### Time Constant Dependence

Saturation time constant depends on precursor vapor pressure and temperature:

```
τ ∝ 1 / P × T
```

Where:
- P = vapor pressure (Torr)
- T = absolute temperature (K)

Or more rigorously (kinetic theory):
```
τ ≈ V / (A × v × σ)
```

Where:
- V = chamber volume
- A = wafer area
- v = molecular velocity = √(8kT / πm)
- σ = sticking coefficient (~0.5-0.9 for chemisorption)

### Saturation Requirement

To achieve 98% coverage (θ = 0.98):

```
0.98 = 1 − exp(−t_pulse / τ)
exp(−t_pulse / τ) = 0.02
−t_pulse / τ = ln(0.02) = −3.9
t_pulse = 3.9 × τ
```

**For ALD cycle optimization:** Pulse time must be ≥ 4τ for reliable saturation.

### Numerical Example: TDMAH at 50°C

- Vapor pressure P(50°C) ≈ 1 Torr
- Boiling point: 160°C → Antoine correlation gives τ ≈ 0.2-0.3 seconds at saturation
- Saturate 98%: t_pulse ≥ 4 × 0.25 = 1 second

**In practice:** Use t_pulse = 0.1-0.2 seconds (conservative; relies on good precursor delivery)

---

## 6. Sputtering Yield & Deposition Rate

### Sputtering Yield Formula

Number of target atoms ejected per incident ion:

```
Y(E) ≈ (α × E) / (E_d + E/3)
```

Where:
- E = ion kinetic energy (eV)
- α = efficiency factor (material-dependent; ~0.1-0.3)
- E_d = displacement energy (~40 eV for Ta)

### Ion Energy from Applied Voltage

Ion kinetic energy equals electron charge times applied voltage:
```
E = e × V_bias
```

For typical sputtering: V_bias = −800V → E = 800 eV

### Deposition Rate Calculation

Using Faraday-like relationship:
```
Deposition rate (nm/min) = (Y × i × M) / (ρ × 60 × 1.6 × 10⁻¹⁹)
```

Where:
- Y = sputtering yield
- i = ion current density (A/cm²)
- M = target molar mass (g/mol)
- ρ = target density (g/cm³)
- 1.6 × 10⁻¹⁹ = charge per electron (C)

### Numerical Example: Tantalum Sputtering

At 800 eV ion energy:
```
Y = (0.2 × 800) / (40 + 800/3)
  = 160 / 310
  ≈ 0.52 atoms/ion
```

For i = 10 mA/cm²:
```
Rate = (0.52 × 0.01 × 180.95) / (16.65 × 60 × 1.6 × 10⁻¹⁹)
     = 0.94 / (1.6 × 10⁻¹⁷)
     ≈ 5.9 nm/min
```

**PVD deposition rate for Ta: ~6 nm/min (10-20x slower than CVD).**

---

## 7. Thermal Interface Material (TIM) Heat Dissipation

### Heat Flow Through TIM

Thermal resistance (analogy to electrical resistance):

```
R_thermal = t / (κ × A)
```

Where:
- R_thermal = thermal resistance (K/W)
- t = TIM thickness (m)
- κ = thermal conductivity (W/m·K)
- A = contact area (m²)

### Junction-to-Ambient Temperature Rise

Total temperature rise:
```
ΔT = P × (R_junction + R_TIM + R_spreader + R_ambient)
```

Where P = power dissipation (W).

### Numerical Example: NVIDIA H100 GPU

Specifications:
- P = 500 W (power dissipation)
- κ (liquid metal TIM) = 70 W/m·K
- t = 0.1 mm = 1 × 10⁻⁴ m
- A = 5 cm² = 5 × 10⁻⁴ m²

**TIM thermal resistance:**
```
R_TIM = (1 × 10⁻⁴) / (70 × 5 × 10⁻⁴)
      = 1 × 10⁻⁴ / 0.035
      = 2.86 × 10⁻³ K/W
      ≈ 0.003 K/W
```

**Temperature rise across TIM alone:**
```
ΔT = 500 W × 0.003 K/W = 1.5 K
```

**With silicon grease (κ = 2 W/m·K):**
```
R_TIM = 1 × 10⁻⁴ / (2 × 5 × 10⁻⁴) = 0.1 K/W
ΔT = 500 × 0.1 = 50 K
```

**Conclusion:** Material choice (liquid metal vs. silicone grease) determines thermal performance; 50K difference is critical for reliability.

---

## Summary Table: Key Constants & Formulas

| Quantity | Formula | Units | Typical Value |
|---|---|---|---|
| **Arrhenius rate** | k = A × exp(−Ea/RT) | s⁻¹ | 0.01-1 s⁻¹ (CVD) |
| **EOT scaling** | EOT = t_hk / κ_rel | nm | 0.4-0.8 nm (sub-3nm) |
| **Electromigration** | MTF = K/j² × exp(Ea/kT) | hours | 1,000+ hours (target) |
| **Faraday deposition** | Rate = M × i / (n × F × ρ) | nm/min | 2-5 nm/min (copper) |
| **ALD saturation** | θ = 1 − exp(−t/τ) | dimensionless | τ ≈ 0.1-0.5 sec |
| **Sputtering yield** | Y = (α × E) / (E_d + E/3) | atoms/ion | 0.5-1.5 atoms/ion |
| **Thermal resistance** | R = t / (κ × A) | K/W | 0.003-0.1 K/W (TIM) |

---

**End of Mathematical Derivations**

These rigorous derivations underpin all process physics discussed in Chapters 1-8. Students and engineers should reproduce these calculations for other materials and conditions.
