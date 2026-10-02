# Chapter 3: Electrodeposition of Copper & Barrier Layers

## Why Copper Is Inevitable

Aluminum interconnects (used for 28nm and above) have a fundamental problem: **electromigration.** Aluminum atoms migrate under electric field, opening circuits.

Tungsten plugs (used for via fill at 22nm-14nm) have a different problem: **resistance.** Tungsten resistivity is 5-10x higher than copper. At sub-2nm nodes, interconnect RC delay dominates logic delay. Copper is non-negotiable.

But copper has a fatal flaw: **it diffuses into silicon.** A copper atom in silicon acts as a recombination center, destroying device performance.

The solution: **Copper with a thin tantalum or tungsten barrier layer.**

This requires electroplating copper after barrier deposition. This chapter explains why electrochemistry—not device physics, not lithography—is now the limiting factor in sub-2nm scaling.

---

## I. Inversion: The Copper Catastrophes

### Failure 1: Via Void Formation

Copper electrodeposition occurs inside a via (vertical trench). If plating chemistry is wrong, voids form—bubbles of unfilled space inside the via.

**Physics of void nucleation:**

During electroplating, hydrogen gas is produced as a side reaction:
```
2 H⁺ + 2 e⁻ → H₂(g)
```

If hydrogen bubbles nucleate on the via sidewall, they create gas pockets. If bubble does not escape before plating completes, the bubble remains as a void.

**Catastrophic consequence:**

A 10 million-via interconnect with 1% void failure rate = 100,000 open circuits. Yield drops to zero.

At sub-2nm pitch (30-40nm via pitch), voids are common unless plating chemistry includes:
1. Suppressor additives (polyethylene glycol) that inhibit plating
2. Accelerator additives (bis-dithiocarbamate) that enhance plating
3. Leveling additives that suppress plating on protrusions

Without the right additive cocktail, **yield catastrophically fails.**

### Failure 2: Barrier Integrity Loss at Atomic Scales

Tantalum barrier thickness for sub-2nm nodes: **2-5 nm** (10-25 atomic layers).

If barrier thickness varies by ±1 nm, copper diffusion rate varies 10x.

**Mechanism:** Copper diffusion follows Arrhenius:
```
D(T) = D₀ × exp(-Ea / RT)
```

With Ea ~0.5 eV and T=400K (operating temp):
- Barrier 5 nm: Copper diffusion timescale ~1,000 years
- Barrier 4 nm: ~100 years (10x faster)
- Barrier 3 nm: ~10 years (100x faster)

**Failure mode:** After 1-5 years of field operation, copper diffuses through thin barrier regions into silicon. Devices fail catastrophically.

### Failure 3: Copper Contamination in Gate Dielectric

If copper drifts into the gate dielectric (HfO₂), device performance is destroyed:
- Copper creates trap sites → leakage current surges
- Fermi level shift → threshold voltage drift
- Reliability → TDDB (time-dependent dielectric breakdown) time drops 100x

**Yield consequence:** Fab cannot sell chips if gate dielectric is contaminated.

### Failure 4: Electromigration at Via Interfaces

Once copper is deposited, electromigration becomes the reliability challenge.

Under electric field (10⁶ A/cm² current density), copper atoms migrate. If migration is unconstrained, vias open up in 1,000-5,000 hours.

**Solution:** Alloying copper with other metals (manganese, cobalt) increases electromigration resistance. But alloying adds process complexity.

---

## II. Physics: Electrochemistry & Plating Kinetics

### A. Electrodeposition Mechanism

**Basic electrochemistry:**
```
Anode (oxidation):    Cu → Cu²⁺ + 2e⁻
Cathode (reduction):  Cu²⁺ + 2e⁻ → Cu
```

**Electrochemical potential (Nernst equation):**
```
E = E₀ + (RT/nF) × ln([Cu²⁺])
```

Where:
- E₀ = standard electrode potential (~+0.34V vs. SHE)
- R = gas constant
- T = temperature
- n = electrons transferred (2 for Cu²⁺)
- F = Faraday constant
- [Cu²⁺] = copper ion concentration

**Practical consequence:** Plating voltage controls deposition rate and uniformity.

---

### B. Plating Current Density & Rate

**Faraday's Law (deposition rate):**
```
Deposition rate (nm/min) = (M × i) / (n × F × ρ)
```

Where:
- M = molar mass of Cu (63.5 g/mol)
- i = current density (A/cm²)
- n = electrons transferred (2)
- F = Faraday constant (96,485 C/mol)
- ρ = copper density (8.96 g/cm³)

**Numerical example:**
- i = 10 mA/cm² (typical)
- Deposition rate = (63.5 × 10) / (2 × 96,485 × 8.96) = ~0.037 nm per second = **2.2 nm/min**

**Practical:** Full via (1 μm deep) fills in ~450 seconds = **7.5 minutes per wafer.**

---

### C. Hydrogen Evolution & Void Risk

**Side reaction (hydrogen evolution):**
```
2 H⁺ + 2 e⁻ → H₂(g)   E₀ = −0.41V
```

At typical plating potentials (−0.2 to −0.5V), hydrogen evolution is suppressed but occurs.

**Hydrogen overpotential** determines suppression efficiency:
```
η = E − E₀ = (RT/nF) × ln(i / i₀)
```

Where i₀ = exchange current density (~1 μA/cm² for copper).

**Consequence:** Higher current density → higher overpotential → more hydrogen suppression → fewer voids.

**Tradeoff:** High current density accelerates deposition but increases temperature rise and copper grain coarsening.

---

### D. Additive Chemistry

**Three classes of additives:**

1. **Suppressors (polyethylene glycol, PEG):** Adsorb on cathode surface, slow down deposition
   - Effect: Leveling (smooth, uniform deposit)
   - Trade: Slower overall deposition rate

2. **Accelerators (bis-dithiocarbamate):** Enhance deposition at high-field regions
   - Effect: Fills deep trenches preferentially (superconformal filling)
   - Trade: Must be carefully dosed to avoid bumping at trench mouth

3. **Levelers:** Suppress deposition on protrusions
   - Effect: Prevents overfill and dishing (via recess)
   - Trade: Complexity; requires tight concentration control

**Optimal additive combination:** A carefully tuned "cocktail" of suppressor:accelerator:leveler ratio (typically 100:10:1).

---

## III. Practice: Electroplating Equipment & Process

### Via Geometry & Aspect Ratio

**Sub-2nm nodes:** Via pitch = 30-40 nm; via depth = 300-500 nm.
- **Aspect ratio:** 500 nm / 30 nm = ~16:1 (extremely high)
- **Challenge:** Electrochemistry must fill deep, narrow trenches uniformly

### Equipment Design: The Plating Cell

**Components:**
1. **Copper anode:** Pure copper disk (dissolves to supply Cu²⁺)
2. **Cathode:** Silicon wafer (where plating occurs)
3. **Electrolyte:** CuSO₄ + H₂SO₄ + organic additives
4. **Circulation pump:** Maintains electrolyte motion (mass transport)
5. **Potential control:** Potentiostat (maintains constant voltage or current density)

**Circulating electrolyte:** Removes hydrogen bubbles, replenishes Cu²⁺, removes byproducts.

### Process Parameters

| Parameter | Typical Value | Impact |
|---|---|---|
| Current density | 10-50 mA/cm² | Higher = faster deposition, more hydrogen evolution |
| Voltage | −0.2 to −0.5 V | Controls overpotential; higher = less void risk |
| Temperature | 20-40°C | Higher = faster kinetics; lower = better additive stability |
| Electrolyte flow | 50-200 mL/min | Higher = better mass transport, fewer voids |
| PEG concentration | 10-20 g/L | Higher = more leveling, slower deposition |
| Accelerator (BDT) | 0.5-2 g/L | Higher = more via fill, risk of surface roughness |

---

## IV. Economics: Via Fill as the Yield Bottleneck

### Yield Impact of Void Formation

**Model:** Assume 10M vias per die, 30-nm pitch.

| Void Fraction | Yield Impact | Fab Consequence |
|---|---|---|
| 0.1% | ~1% of dies have open via → ~99% yield | Acceptable |
| 1% | ~10% of dies affected → ~90% yield | Marginal |
| 3% | ~25% of dies affected → ~75% yield | Unacceptable; production halt |

**Cost per failed wafer:** $10K-50K (lost revenue + rework).

**Solution:** Optimize plating additive chemistry to achieve <0.5% void fraction.

**Development cost:** $1-5M (empirical optimization across 100+ additive cocktails).

### Equipment Cost & Service Revenue

**Electroplating equipment (Novellus Nova™, Lam Corona™):**
- **Capital cost:** $1.5-3M per system
- **Throughput:** ~200-300 wafers/day (parallel processing)
- **Tool lifetime:** 5-7 years
- **Service cost:** $200-400K/year (maintenance, additives, anode consumption)

**Service margin:** 65-70% (consumables cost is low; anode replacement ~$50-100K/year).

---

## V. Capital Allocation: Why Copper Plating Vendors Are Valuable

### Market Size

**Electroplating market (2024-2028):**
- Current TAM: ~$500M-$700M
- Growth driver: Via fill complexity at sub-3nm nodes
- Projected CAGR: 12-15%
- 2028 TAM: ~$1B+

**Equipment vendors (Novellus, Lam, AMAT):**
- Combined market share: 85%+
- Average system lifespan: 5-7 years
- Service revenue per system: $200-400K/year

### ROIC Calculation

**Per electroplating system:**
- Equipment capex: $2.5M
- Annual service revenue: $300K
- Service gross margin: 68%
- Service gross profit/year: $200K

**7-year cumulative:**
- Equipment gross profit: $500K (20% of capex)
- Service gross profit: $1.4M (7 × $200K)
- **Total gross profit: $1.9M on $2.5M capex = 76% gross return**
- **Annualized IRR: ~12-15%**

**ROIC (operating profit / invested capital):**
- Lam's electroplating division: 32-38% (lower than lithography, higher than foundries)

**Why is electroplating less profitable than lithography?**
1. Equipment cost is lower ($2.5M vs. $5-10M for lithography)
2. Service revenue is lower ($300K/year vs. $1M+/year for lithography)
3. Market is less mature; more competition

**But why is it more valuable than it appears?**
1. **Barrier to entry:** Chemical additives formulations are proprietary; competitors need 18-24 months to develop competitive recipes
2. **Customer lock-in:** Once a customer qualifies a plating chemistry, switching costs are ~$2-5M (re-qualification across 100+ tests)
3. **Node-dependent:** Every new node requires new additive recipes; equipment vendors control this IP

---

## VI. The Barrier Layer: Tantalum & Tungsten

Before copper plating, a barrier layer (tantalum or tungsten) is deposited via PVD.

**Barrier requirements:**
1. **Thickness:** 2-5 nm (atomic precision)
2. **Conformality:** Must follow trench walls perfectly (±0.5 nm)
3. **Uniformity:** Edge-to-center thickness variation <10%

**Barrier materials:**
- **Tantalum (Ta):** Resistivity ~1,000-2,000 μΩ-cm (better than tungsten); easier to etch; preferred
- **Tungsten (W):** Resistivity ~50 μΩ-cm (lower, but thicker barriers needed); used in some processes

**Economics:** Barrier material cost ~$5-20/wafer; not significant cost driver. **Process IP is the moat.**

---

## VII. Electromigration & Reliability

Once copper is deposited, **electromigration** becomes the reliability challenge.

Under current stress (10⁶ A/cm² in sub-2nm nodes), copper atoms migrate preferentially in the direction of electron flow (wind force + thermal gradient).

**Electromigration current density limit (Black's equation):**
```
MTF (hours) ∝ (1 / j^n) × exp(Ea / kT)
```

Where:
- j = current density (A/cm²)
- n = exponent (typically 2)
- Ea = activation energy (~0.7-0.9 eV for copper)
- k = Boltzmann constant
- T = absolute temperature

**Example:**
- At j = 10⁶ A/cm², T = 400K: MTF ~1,000 hours (unacceptable)
- Solution: Alloy copper with manganese/cobalt to increase Ea

**Alloyed copper (Cu-Mn, Cu-Co):**
- Electromigration resistance increased 3-5x
- Cost increase: ~10-20% (additive chemistry complexity)
- Trade: Resistivity increase ~5-10% (minor impact)

---

**Next:** [Chapter 4: PVD & Sputtering: Ballistic Material Transport](04-pvd-sputtering.md)
