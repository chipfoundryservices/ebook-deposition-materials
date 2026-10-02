# Chapter 6: ALD & Atomic Layer Control

## Why One Atom Matters

At 3nm nodes, the gate dielectric is 10 nm thick—roughly 30 atomic layers.

If each layer thickness varies by ±1 atom (0.3 nm), **the dielectric has ±3% thickness variation.**

±3% thickness variation = ±9% capacitance variation = ±15% device performance variation = **yield catastrophe.**

**Only ALD can deposit with atomic precision.**

CVD has ±5-10% variation. Sputtering has ±10-20% variation. ALD achieves ±0 nm variation (truly monolayer-by-monolayer control).

This chapter reveals why ALD is the future of semiconductor deposition, and why ALD equipment vendors will capture the highest ROIC of any equipment company by 2030.

---

## I. Inversion: The Atomic Control Failures

### Failure 1: Incomplete Monolayer Coverage

ALD relies on **self-limiting surface reactions:** once the surface is saturated with precursor, no more precursor sticks.

**But "saturation" is probabilistic.** Not every surface site captures a precursor molecule.

**Coverage rate:**
- Ideal (100% monolayer coverage): Thickness = 0.30 nm per cycle
- Real (95% coverage): Thickness = 0.285 nm per cycle
- Real (85% coverage): Thickness = 0.255 nm per cycle

**Cascading effect:** Over 33 cycles:
- Ideal: 33 × 0.30 = 9.9 nm
- Real (85%): 33 × 0.255 = 8.415 nm

**Thickness error:** 1.5 nm over 10 nm target = 15% error!

**Prevention:** Optimize temperature and precursor pulse time to achieve >98% coverage per cycle.

### Failure 2: Thermal Decomposition at Temperature

ALD must operate at low temperature (200-300°C for gate dielectrics) to preserve underlying layers.

**But at temperature, adsorbed precursor molecules can decompose thermally before water reacts with them:**

```
Step 1: HfN(CH₃)₂]₄ adsorbs on surface (normal)
Step 2: HfN(CH₃)₂]₃ decomposes by thermal cleavage → Hf(NMe₂)₃ leaves surface
Step 3: H₂O pulse arrives; fewer Hf sites available to react
Result: Monolayer incomplete
```

**Temperature trade-off:**
- 150°C: Precursor very stable; low thermal decomposition; BUT precursor saturation is slow
- 250°C: Precursor saturation fast; BUT thermal decomposition begins
- 350°C: Fast saturation; significant decomposition; film quality suffers

**Optimal window:** 200-250°C (narrow; must be tightly controlled).

### Failure 3: Water Vapor Contamination

H₂O co-reactant must be ultrapure. **Any moisture contamination creates extra oxygen vacancies.**

**Impurities in water supply:**
- CO₂ (from air): Forms carbonate species on surface
- H₂SO₄ (from storage): Creates sulfur impurities
- Organic solvents: Create carbon impurities

**Result:** HfO₂ film contains O vacancies → trap sites → leakage current.

**Specification:** Ultrapure water <1 ppb (parts per billion) impurities.

**Cost:** Ultrapure water ~$10-50 per liter (vs. $0.01 for ordinary water).

### Failure 4: Precursor Vapor Pressure Insufficiency

ALD requires precursor to **saturate the surface** (every available site captures a molecule).

Saturation requires minimum **vapor pressure.**

**Problem:** Some precursors have low vapor pressure at room temperature.

**Example: Tetrakis(dimethylamino)hafnium (TDMAH)**
- Boiling point: 160°C
- Vapor pressure at 25°C: ~0.1 Torr (very low)
- Vapor pressure at 50°C: ~1 Torr (adequate)

**Solution:** **Precursor heating** (bubblers kept at 40-60°C to increase vapor pressure).

**Trade:** Heating requires additional equipment; adds process complexity.

---

## II. Physics: Self-Limiting Reactions & Saturation

### A. Chemisorption & Monolayer Formation

**Step 1: Precursor adsorption**

When hafnium precursor HfN(CH₃)₂]₄ enters ALD chamber:
```
Si-OH (surface site) + HfN(CH₃)₂]₄ → Si-O-Hf(N(CH₃)₂)₃ + HN(CH₃)₂ (gas)
```

**Mechanism:** Nucleophilic attack by surface OH group on Hf center.

**Binding:** Hf-O bond energy ~800 kJ/mol (strong, irreversible under ALD conditions).

**Consequence:** Once one Hf is bonded, surface site is "occupied" and no more Hf can stick there.

**Saturation:** After all sites are occupied, no more Hf adsorbs (self-limiting).

**Monolayer thickness:** 0.3-0.4 nm per cycle (consistent, precisely controllable).

### B. Surface Saturation Kinetics

**Adsorption follows Langmuir kinetics:**
```
θ(t) = θ_sat × [1 − exp(−t / τ)]
```

Where:
- θ = fractional surface coverage (0 to 1)
- θ_sat = maximum coverage (~1 monolayer)
- τ = time constant for saturation
- t = exposure time

**Time constant τ depends on:**
- Precursor vapor pressure P (higher P → smaller τ)
- Surface temperature T (higher T → smaller τ)
- Surface site density N (more sites → larger τ)

**Practical:** τ ranges from 0.1-1 second (depends on precursor and condition).

**Implication:** To achieve 98% saturation (θ = 0.98), exposure time must be ≥ 4τ.

### C. Water Co-Reactant Pulse

**Step 2: Water pulse**

When ultrapure H₂O enters chamber:
```
Si-O-Hf(N(CH₃)₂)₃ + H₂O → Si-O-Hf-OH + H-N(CH₃)₂ (gas) + products
```

**Mechanism:** Nucleophilic attack by water oxygen on Hf, breaking Hf-N bonds.

**Product:** Hafnium hydroxide/oxide on surface; ligands (dimethylamino groups) leave as gas.

**Consequence:** Surface now has Hf-OH groups, ready for next cycle.

**Reaction time:** Typically fast (0.05-0.5 seconds); limited by diffusion of H₂O to reactive sites.

### D. Purge Steps (Critical for Selectivity)

**Between precursor and water pulses, chamber is purged with inert gas (N₂ or Ar).**

**Purpose:** Remove excess precursor from gas phase.

**If purge is insufficient:**
- Residual precursor remains in gas phase
- Water encounters residual precursor in gas phase
- Unwanted gas-phase CVD reactions occur
- Film quality degrades

**Purge requirement:** Must remove >99.9% of precursor.

**Duration:** Depends on chamber volume and pump speed. Typical: 2-5 seconds per purge.

**Consequence:** ALD cycle time is slow.

---

## III. Practice: ALD Chamber Design & Pulse Sequence

### Spatial vs. Temporal ALD

**Temporal ALD (standard):**
- Precursor pulse → Saturate surface (1 second)
- Purge → Remove excess (3 seconds)
- Water pulse → React (1 second)
- Purge → Remove water (3 seconds)
- **Cycle time:** 8 seconds
- **Throughput:** 450 wafers per cycle hour = **7.5 wafers per minute** (for single wafer)

**Spatial ALD (emerging):**
- Instead of time-based pulses, use **physical separation** of precursor and water zones
- Precursor zone, purge zone, water zone, purge zone arranged in chamber
- Wafer moves through zones continuously
- **Cycle time:** Continuous (no discrete cycles)
- **Throughput:** 10-20 wafers per minute (2-3x faster)

**Trade:** Spatial ALD is more complex; currently only for high-volume production (NAND flash).

### Equipment Architecture (Temporal ALD)

**Lam ALD system components:**

1. **Precursor delivery:** Heated bubbler maintains 40-60°C
2. **Purge line:** Inert gas (N₂, ultrapure)
3. **Reaction chamber:** Heated to 200-300°C; volume ~5-50 liters
4. **Pump:** Vacuum pump (1-10 Torr during operation)
5. **Exhaust scrubber:** Neutralizes toxic byproducts (HN(CH₃)₂ is volatile, hazardous)

### Cycle Optimization

**Challenge:** Minimize cycle time while maintaining >98% coverage.

**Optimized cycle:**
- Precursor pulse: 0.2 sec (adequate saturation at 50°C bubbler temp)
- Purge 1: 2 sec
- Water pulse: 0.1 sec (water is very reactive; fast reaction)
- Purge 2: 2 sec
- **Total:** 4.4 sec/cycle (vs. standard 8 sec)

**Impact:** 4.4 sec/cycle → ~820 wafers/hour/chamber vs. 450 wafers/hour (82% throughput improvement).

---

## IV. Economics: ALD Capacity & Bottlenecks

### Fab Throughput Requirements

**Sub-3nm fab producing 50,000 wafers per month:**

Gate dielectric layers per wafer:
- One HfO₂ layer per transistor (gate-all-around requires 2-3 layers due to multiple gates)
- Average: 2 layers × 33 cycles × 4.4 sec/cycle = 290 seconds per wafer
- Convert to wafer throughput: (3,600 sec/hr) / (290 sec/wafer) = **12.4 wafers/hour per tool**

**Required ALD tools (for 50,000 wafers/month capacity):**
- 50,000 wafers/month = 2,083 wafers/day = 173 wafers/hour
- Tools needed: 173 / 12.4 = **14 ALD tools**

**Equipment capex:** 14 × $3M = **$42M**

**This is not trivial.** A single fab requires ~14 ALD tools just for gate dielectrics (plus additional ALD tools for conformal layers, 3D NAND, etc.).

### ALD Equipment Market Size

**Global fab capacity at sub-3nm (2024-2028):**
- Current (2024): ~500K wafers/month (TSMC, Samsung, Intel combined)
- Projected (2028): ~2M wafers/month (new fabs ramp)

**ALD tools needed:**
- 2024: 500K / 1,500 (wafers/tool/month) × 0.5 (ALD fraction) = ~167 tools
- 2028: 2M / 1,500 × 0.7 (ALD fraction increases) = ~933 tools

**Equipment revenue (assuming average price $3M/tool):**
- 2024: 167 × $3M = $500M
- 2028: 933 × $3M = $2.8B
- **5-year cumulative:** ~$10B ALD equipment market

**Equipment vendor share (Lam, AMAT, TEL):**
- Gross margin: 50-55%
- **5-year cumulative gross profit:** $5-5.5B across all vendors

---

## V. Capital Allocation: Why ALD Vendors Win

### Long-Term Installed Base Value

Unlike lithography (ASML) or etch (Lam), ALD equipment vendors have been small players.

But by 2028:
- Installed base of ALD tools will reach ~2,000+ globally
- Each tool generates $400-600K annual service revenue
- Service margin: 50-60%
- Service gross profit per tool: $200-300K/year

**Installed base value (at 2028):**
- 2,000 tools × $250K service gross profit = **$500M annual service revenue**
- Capitalized at 20x multiple: **$10B company value** from service revenue alone

### Precursor Supply Chain Lock-In

Precursor suppliers (Air Liquide, Honeywell) are gatekeepers:

**Global TDMAH supply:** ~500K liters/year (2024) → ~2M liters/year (2028).

**Precursor cost:** $150/liter (after scaling)

**Annual precursor market (2028):** 2M liters × $150 = **$300M**

**Precursor supplier gross margin:** 70-75%

**Gross profit:** $210-225M annually (2028)

**5-year cumulative (2024-2028):** ~$700-800M gross profit

**Precursor suppliers are virtually guaranteed recurring revenue for 5-7 years** as ALD capacity ramps.

---

## VI. Process Window & Yield

### Cycle-to-Cycle Consistency

ALD's main advantage is **monolayer-by-monolayer consistency.**

**Repeatability specification:**
- Thickness per cycle: 0.30 ± 0.01 nm (3.3% variation)
- Over 33 cycles: 9.9 ± 0.33 nm (3.3% variation)
- Equivalent to ±0.15 atomic layers per cycle (exceptional precision)

**CVD comparison:**
- CVD thickness variation: ±10-15% (vs. ALD's ±3%)

**Economic impact:** Tighter process window → fewer wafers scrapped for thickness out-of-spec.

### Temperature Stability

ALD chamber temperature must be stable to ±1°C for high-quality deposits.

**Equipment specification:** Thermal stability ±0.5°C (better than required).

**Cost:** Temperature control adds ~$200K-300K to tool cost (resistance heaters, thermocouples, feedback control).

---

## VII. The ALD Supercycle (2025-2030)

ALD is currently in its infancy relative to lithography (ASML) or etch (Lam).

**But 2025-2030 will see explosive ALD growth:**

| Year | Sub-3nm Wafers/Month | ALD Tools Needed | Equipment Revenue |
|---|---|---|---|
| 2024 | 500K | 167 | $500M |
| 2025 | 700K | 233 | $700M |
| 2026 | 1,000K | 333 | $1B |
| 2027 | 1,500K | 500 | $1.5B |
| 2028 | 2,000K | 667 | $2B |

**5-year revenue:** ~$7.2B

**Gross profit at 50% margin:** ~$3.6B

**Per vendor (assuming 4 major players):** ~$900M gross profit each

**This is comparable to ASML's annual gross profit today ($2-3B).**

---

**Next:** [Chapter 7: Equipment Engineering & Materials Moats](07-equipment-moats.md)
