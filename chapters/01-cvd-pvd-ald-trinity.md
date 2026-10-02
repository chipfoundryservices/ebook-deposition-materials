# Chapter 1: The CVD/PVD/ALD Trinity

## The Three Deposition Paradigms

Semiconductor manufacturers have three—and only three—ways to deposit films at sub-100nm precision:

1. **CVD (Chemical Vapor Deposition):** Gas-phase precursors react on a hot surface to form solid film
2. **PVD (Physical Vapor Deposition):** Energetic atoms knocked off a target; they travel through vacuum and condense
3. **ALD (Atomic Layer Deposition):** Sequential, self-limiting surface reactions; one atomic layer per cycle

Each is irreplaceable. Each owns a specific segment of the manufacturing roadmap.

This chapter establishes why understanding these three paradigms is essential for predicting equipment capex cycles, materials supply constraints, and competitive advantages over the next 5-7 years.

---

## I. Inversion: What Destroys Each Method?

### CVD Failure Modes

**Problem 1: Precursor Depletion & Reactant Starvation**

CVD requires gaseous precursors (silane, tungsten hexafluoride, trimethylaluminum). If precursor supply fails—if a single chemical supplier has production problems—fab capex cycles collapse for 12-18 months while new suppliers are qualified.

**Problem 2: Byproduct Accumulation & Chamber Poisoning**

CVD reactions produce byproducts (silane produces silane oligomers, tungsten hexafluoride produces WF₄, HF). If byproducts accumulate on chamber walls, film uniformity degrades. Chamber cleaning becomes a bottleneck.

**Problem 3: Thermal Budget Explosion**

CVD often requires 400-800°C chamber temperatures. At sub-2nm nodes, this thermal budget conflicts with integrated metal layers and gate stacks. Temperature is irreplaceable; you cannot deposit tungsten at 200°C using CVD.

### PVD Failure Modes

**Problem 1: Step Coverage at Deep Structures**

In PVD, atoms travel in straight lines from target to substrate (ballistic transport). They cannot follow deep trenches. A 3:1 aspect-ratio trench means PVD deposits 3x thinner at the bottom than at the top. This is catastrophic for interconnect uniformity.

**Problem 2: Contamination from Target Sputtering**

When sputtering a target (e.g., tungsten), impurities in the target (oxygen, carbon) are also sputtered. They co-deposit with the film, degrading its properties.

**Problem 3: Throughput Limits**

PVD deposition rates are slow (~10 nm/min vs. CVD's ~100 nm/min). For thick films (copper bumps, solder), PVD is uneconomical.

### ALD Failure Modes

**Problem 1: Precursor Saturation Limits**

ALD relies on precursor saturation: molecules must chemisorb on the surface until saturated. If precursor vapor pressure is too low, saturation fails. Temperature determines vapor pressure; if temperature is wrong, yield collapses.

**Problem 2: Cycle Time Explosion at Scale**

ALD deposits one atomic layer per cycle. For a 100nm film, you need 300+ cycles. At ~3 seconds per cycle, ALD takes 15+ minutes per die. This is uneconomical for thick films.

**Problem 3: Co-Reactant Purity**

ALD for oxides (HfO₂, Al₂O₃) requires pure water or oxygen as co-reactant. A single contamination event (moisture in precursor, air in the chamber) destroys the entire batch.

These are not minor engineering challenges. **They are existential constraints that determine which deposition technology is used for each layer.**

---

## II. Physics: The Three Mechanisms

### CVD: Gas-Phase Reactions

**General reaction:**
```
Precursor(g) + Reducing agent(g) → Film(s) + Byproducts(g)
```

**Energy source:** Thermal energy or plasma.

**Mechanism:**
1. Precursor molecules enter chamber as gas
2. Heat or plasma provides activation energy for decomposition
3. Reactive fragments stick to substrate and react
4. Byproducts desorb as gas
5. Product film grows perpendicular to substrate

**Examples:**
- Tungsten CVD: WF₆ + 3 H₂ → W + 6 HF (requires ~400°C)
- Silicon CVD: SiH₄ → Si + 2 H₂ (requires ~600°C)
- Copper CVD: Cu(TMVS) + H₂ → Cu + byproducts (emerging; still development stage)

**Advantages:**
- Excellent step coverage (gas fills deep trenches)
- Fast deposition (~50-200 nm/min)
- Uniform across wafer
- No line-of-sight constraint

**Disadvantages:**
- High temperature (300-1000°C) incompatible with low-K dielectrics
- Precursor toxicity & supply chain constraints
- Byproduct management (HF, WF₄ corrosive and difficult to handle)
- Thermal budget limits (cannot deposit after metal patterning)

---

### PVD: Ballistic Transport

**General mechanism:**
```
Target atoms sputtered by energetic ion bombardment
↓
Travel through vacuum (no collisions)
↓
Condense on substrate
```

**Energy source:** DC or RF plasma; target voltage −500 to −2000V relative to substrate.

**Mechanism:**
1. Inert gas (Ar) ionized to Ar⁺ in plasma
2. Ar⁺ accelerated toward negatively biased target
3. Impact knocks target atoms loose (sputtering)
4. Target atoms travel through vacuum without collisions (mean free path >> chamber size)
5. Atoms condense on substrate (thermal + kinetic energy)

**Sputtering yield (atoms per ion):**
- Tungsten: ~1 atom/ion (hard target)
- Aluminum: ~0.5 atoms/ion (softer target)
- Copper: ~1.5 atoms/ion

**Advantages:**
- Works at room temperature (no thermal budget)
- Excellent adhesion (energetic atoms bond strongly)
- Can sputter virtually any material
- No toxic precursor chemicals

**Disadvantages:**
- Ballistic transport = poor step coverage (line-of-sight only)
- Slow deposition (~10 nm/min for metals)
- Substrate temperature rises from ion bombardment (secondary effect)
- Target contamination co-deposits with film

---

### ALD: Self-Limiting Surface Reactions

**General mechanism:**
```
Cycle 1:  Precursor A saturates surface → Self-limiting monolayer
Purge:    Remove excess A from gas phase
Cycle 2:  Reactant B reacts with adsorbed A → One atomic layer forms
Purge:    Remove B from gas phase
Repeat:   N cycles → N atomic layers
```

**Mechanism (Al₂O₃ example):**
1. Trimethylaluminum (TMA) pulse: Al(CH₃)₃ → Al-CH₃ bonds to surface OH groups
   - Self-limiting: once surface covered, no more TMA sticks (chemisorption limited by surface sites)
2. Purge with inert gas (N₂, Ar): removes unreacted TMA
3. H₂O pulse: H₂O reacts with Al-CH₃ → Al-OH + byproducts (CH₄)
   - Regenerates OH groups for next cycle
4. Purge with inert gas
5. Repeat: Each cycle adds ~1 Ångstrom Al₂O₃

**Advantages:**
- **Atomic-scale uniformity** (perfect conformality, ±0 nm variation across trench)
- Works at low temperature (50-300°C)
- Pinhole-free (surface chemistry guarantees complete coverage)
- Excellent for ultrathin films (~1-10 nm) and conformal coating

**Disadvantages:**
- **Extremely slow:** 1 Å per cycle, ~3 sec/cycle → ~100 nm/min (10x slower than CVD)
- Cannot deposit thick films economically
- Precursor toxicity (TMA ignites in air, pyrophoric)
- Co-reactant purity critical (water must be ultrapure)

---

## III. Practice: The Equipment Landscape

### CVD Equipment: Lam, AMAT, TEL

**Market leader: Lam Research**

Lam dominates CVD because they own the chemistry IP:
- Tungsten CVD: Proprietary H₂ reduction at ~400°C (optimized for via fill)
- Chamber design: Uniform gas flow, byproduct management, thermal control
- Process know-how: Recipe database for 22nm → 3nm nodes

**Lam's Ultima™ platform:** $3-5M per system
- 300mm wafer capability
- ~10,000 wafers/year throughput per tool
- Service revenue: $0.5-1M/year (consumables, maintenance)
- Installed base: 900+ systems globally

---

### PVD Equipment: Raytheon, Novellus, Lam

**Market leader: Lam Research (through acquisition)**

PVD is fragmented; Lam acquired PVD capability but does not dominate:
- Cathode design: Optimizing sputtering uniformity
- Deposition rate: ~20-50 nm/min for metals
- Step coverage: ~30-50% at 3:1 aspect ratio (adequate for barrier/seed layers)

**Lam's PVD systems:** $2-3M per system
- Vacuum chamber technology
- Ion bombardment control
- Throughput: ~5,000 wafers/year (slower than CVD)

---

### ALD Equipment: Lam, Wacker Chemie, Ultratech

**Market leader: Lam Research (through acquisition of Novellus)**

ALD is the fastest-growing segment (2024-2028):
- **Total addressable market:** $500M-$1B (and growing)
- **Drivers:** High-κ dielectrics, thin barriers, conformal gate dielectrics at sub-3nm

**Lam's Oxford Instruments™ platform:** $1.5-3M per system
- Precursor delivery precision
- Chamber vacuum stability
- Sequential pulse control (±10 ms timing)
- Installed base: 200+ systems (growing 20%+ annually)

---

## IV. Economics: Why Each Technology Survives

### CVD Economics

**Capex:** $3-5M per tool  
**Throughput:** ~10,000 wafers/year  
**Capex cost per wafer:** $300-500/wafer in steady state  
**Gross margin (equipment vendor):** 50-55% ($1.5-2.75M annual gross profit per tool)

**Why it survives:** CVD's step coverage and speed are irreplaceable for thick films (tungsten plugs, copper metallization). Alternatives are 5-10x slower.

### PVD Economics

**Capex:** $2-3M per tool  
**Throughput:** ~5,000 wafers/year (50% slower than CVD)  
**Capex cost per wafer:** $400-600/wafer  
**Gross margin:** 45-50%

**Why it survives:** PVD is only option for room-temperature deposition (barrier/seed layers before copper plating). CVD cannot work at room temperature.

### ALD Economics

**Capex:** $1.5-3M per tool  
**Throughput:** ~3,000-5,000 wafers/year (2-5x slower than CVD)  
**Capex cost per wafer:** $300-1,000/wafer (variable, depends on film thickness)  
**Gross margin:** 50-55%

**Why it survives:** ALD is only option for ultrathin, conformal, pinhole-free films. The $50B/year high-κ dielectric market demands ALD's atomic precision.

---

## V. Capital Allocation: The Equipment Supercycle (2024-2028)

The semiconductor industry is deploying **$30-50B in deposition equipment annually** (2024-2028).

**Why?**

1. **3D NAND scaling:** 100+ layers requires CVD for each oxide-nitride-oxide stack
2. **Chiplet packaging:** Via fill (CVD tungsten) must be perfect to avoid opens
3. **Sub-3nm nodes:** Gate-all-around devices require conformal high-κ (ALD-only)
4. **Advanced interconnect:** 7-8 metal layers per die; ~50% is deposition capex

**Equipment vendor revenue opportunity:**

If fab capex is $40B/year, deposition represents 5-7% of that capex:
- Equipment sales: $2-3B/year (all vendors combined)
- Service revenue: $800M-$1.2B/year (at 40-50% of equipment sales)
- **Total vendor revenue:** $2.8-4.2B/year
- **Gross profit (at 50% margin):** $1.4-2.1B/year

**Per installed system (conservative estimate):**
- Annual service revenue per tool: $0.5-1M
- Service margin: 70-75%
- **Service gross profit per tool:** $350-750K/year
- **Over 7-year equipment lifetime:** $2.5-5M gross profit per tool

This is why Lam Research commands 30-40% ROIC: **high margins + recurring service revenue + long equipment lifetimes.**

---

## VI. The Roadmap Ahead

Each subsequent chapter explores one deposition technology in depth:

- **Chapter 2:** CVD Reaction Kinetics (tungsten, tungsten-copper hybrid)
- **Chapter 3:** Electrodeposition of Copper (electrochemistry, plating chemistry)
- **Chapter 4:** PVD & Sputtering (ballistic transport, film quality)
- **Chapter 5:** High-κ Dielectrics (hafnium oxide, interface engineering)
- **Chapter 6:** ALD & Atomic Layer Control (self-limiting reactions, conformality)

By understanding these three pillars, you will see why deposition is not a commodity—it is a **durable, defensible moat** that only the largest equipment vendors can occupy.

---

**Next:** [Chapter 2: CVD Reaction Kinetics & Chamber Physics](02-cvd-reaction-kinetics.md)
