# Chapter 2: CVD Reaction Kinetics & Chamber Physics

## The Precursor Problem

When you deposit tungsten metal using CVD, you do not deposit tungsten atoms directly. You deposit tungsten hexafluoride (WF₆) gas, which decomposes at 400-600°C to form tungsten and hydrofluoric acid.

The chemistry is elegant. The engineering is brutal.

**The core challenge:** Guarantee that every point on the wafer experiences the same precursor concentration, the same temperature, and the same dwell time. If you deviate by ±5%, film thickness varies by ±15%. If film thickness varies by 15%, electrical resistance varies by 30%. If resistance varies by 30%, **your circuit does not work.**

This chapter reveals why CVD equipment vendors command 30-40% ROIC: they have solved a problem that looks simple but is actually catastrophically complex.

---

## I. Inversion: The Kinetic Failures

### Failure 1: Precursor Decomposition Lag

WF₆ does not decompose instantaneously. At 400°C:
- Decomposition time constant: ~1-2 seconds
- Chamber residence time: ~0.5-2 seconds

If residence time < decomposition time constant, precursor reaches the exhaust without decomposing. Film deposition rate collapses.

Solution: **Optimize temperature and residence time such that decomposition is complete before exhaust.** This is a tightrope: too hot, and deposition shifts to gas-phase (not surface); too cool, and precursor escapes undecomposed.

### Failure 2: Byproduct Redeposition

CVD of tungsten produces HF as byproduct:
```
WF₆ + 3 H₂ → W + 6 HF
```

HF is highly reactive. If HF concentration gets too high, it:
- Etches the film (removing tungsten almost as fast as depositing it)
- Corrodes the chamber walls (creating tungsten contamination)
- Poisons the substrate surface (preventing nucleation on next cycle)

If HF is not removed fast enough, **net deposition rate becomes zero or negative.**

### Failure 3: Temperature Non-Uniformity

A 300mm wafer has thermal gradients:
- Edge exposure to chamber walls: cooler
- Center exposure to heat source: hotter
- Typical edge-to-center gradient: ±5-10°C

This translates directly to deposition rate variation:
- Deposition rate doubles with every ~20-30°C increase (exponential dependence)
- ±10°C gradient → ±30-40% deposition rate variation

Uncontrolled, this destroys uniformity. Fabs reject the wafer.

### Failure 4: Precursor Starvation (Depletion)

As precursor flows across the wafer, it gets consumed. The edge of the wafer sees high precursor concentration; the trailing edge sees depleted concentration.

If precursor concentration at the trailing edge drops by 20%, deposition rate drops by 20-30% (depends on reaction order).

---

## II. Physics: Reaction Kinetics & Transport

### A. Precursor Decomposition (Thermal vs. Plasma)

**Thermal decomposition** (conventional CVD):

Decomposition rate depends on temperature via Arrhenius equation:
```
k(T) = A × exp(-Ea / RT)
```

Where:
- k = decomposition rate constant
- A = pre-exponential factor
- Ea = activation energy (~150-200 kJ/mol for WF₆ decomposition)
- R = 8.314 J/(mol·K)
- T = absolute temperature (K)

**Example: WF₆ decomposition**
- At 400°C (673 K): k = 0.1 s⁻¹ (decomposition time τ = 10 s)
- At 500°C (773 K): k = 0.5 s⁻¹ (decomposition time τ = 2 s)
- At 600°C (873 K): k = 2 s⁻¹ (decomposition time τ = 0.5 s)

**Implication:** Raising temperature by 100°C reduces decomposition time 4x.

**Plasma-enhanced CVD (PECVD):**

Plasma provides activation energy, lowering decomposition temperature to 200-300°C. But plasma adds complexity:
- Radical species (H•, F•) created in plasma zone
- Must diffuse to substrate without recombining
- Chamber design becomes critical

---

### B. Surface Reaction & Nucleation

Once precursor decomposes, reactive fragments (W, WF, F•) approach the substrate. **Surface reactions dominate deposition rate.**

**Tungsten deposition surface reaction:**
```
WF + H → W-H (chemisorption)
W-H + H₂ → W + 2 H (hydrogen extraction)
```

**Activation energy:** ~80-120 kJ/mol (much lower than decomposition).

**Critical parameter:** Surface coverage of adsorbed fragments.

If surface is saturated with W-H intermediates, deposition rate is limited by hydrogen extraction (desorption-limited kinetics). If surface is bare, deposition rate is limited by adsorption (adsorption-limited kinetics).

**Implication:** Deposition rate can be limited by temperature (kinetics) **or** precursor concentration (transport)—depending on regime.

---

### C. Precursor Transport (Convection & Diffusion)

Precursor molecules reach the substrate via two mechanisms:

1. **Convection:** Gas flows across wafer from inlet to exhaust
2. **Diffusion:** Molecules diffuse perpendicular to flow

**Convection-dominated regime (fast flow):**
- Precursor concentration uniform → uniform deposition
- Limited by reaction rate (not transport)

**Diffusion-dominated regime (slow flow):**
- Precursor depleted along flow path → non-uniform deposition
- Limited by diffusion rate (not reaction)

**Transport equation (simplified):**
```
Deposition rate ∝ min(k_reaction × [Precursor], D × ∇[Precursor])
```

Where D = diffusion coefficient.

**Practical implication:** Equipment vendors must balance flow rate (convection) and chamber geometry (diffusion) to avoid starvation.

---

### D. Byproduct Removal

**HF byproduct concentration** builds up as WF₆ decomposes:
```
[HF]_accumulation = ([WF₆]_consumed × 6) / (Gas residence time)
```

If residence time is too long, HF accumulates to levels where:
1. Etch rate becomes significant
2. Net deposition rate = Deposit rate − Etch rate → zero

**Solution:** Optimize exhaust pumping to remove HF efficiently.

**Scrubber chemistry:** HF is neutralized in exhaust scrubber (NaOH bath):
```
HF + NaOH → NaF + H₂O
```

---

## III. Practice: Chamber Design & Process Control

### Chamber Geometry (Horizontal vs. Vertical)

**Horizontal chamber (Lam Ultima™ design):**
- Precursor gas enters horizontally across wafer
- Wafer is horizontal on heated susceptor
- Exhaust exits horizontally on opposite side
- **Advantage:** Uniform flow, controlled residence time, excellent uniformity
- **Disadvantage:** Precursor depletion along flow path still occurs (mitigated by showerhead design)

**Vertical chamber (alternative):**
- Precursor enters from above, exits below
- Wafer vertical or at angle
- **Advantage:** Better for handling multiple wafers stacked
- **Disadvantage:** Gravity effects, less uniform gas distribution

### Temperature Control

**Objective:** Maintain ±1-2°C uniformity across 300mm wafer.

**Methods:**
1. **Resistive heating:** Graphite susceptor with embedded heaters
2. **Thermocouple feedback:** Real-time temperature measurement + active control
3. **Thermal uniformity mapping:** Pre-calibration to find optimal heater power distribution

**Practical specification:**
- Center temperature: 500°C
- Edge temperature: 498-502°C (±2°C)
- Uniformity: ±0.4% (meets ±15% film thickness variation requirement)

### Flow Rate Optimization

**Trade-off between two regimes:**

**High flow rate (convection-dominated):**
- Precursor uniform across wafer → excellent thickness uniformity
- But residence time very short → if decomposition slow, precursor escapes undecomposed
- **Optimal:** 500-2,000 sccm (standard cubic centimeters per minute)

**Low flow rate (diffusion-dominated):**
- Residence time long → complete decomposition
- But precursor depleted by end of wafer → non-uniform thickness
- **Avoid**

**Showerhead design:** Distributes precursor from multiple injection points to maintain uniformity even with moderate flow rates.

---

## IV. Economics: Why CVD Equipment Is Expensive

**Lam Research Ultima™ CVD system:**
- **Capital cost:** $3-5 million
- **Throughput:** ~10,000 wafers/year
- **Tool lifetime:** 7-10 years (~70,000-100,000 wafers)

**Cost per wafer (capex amortization):** $30-50/wafer

**But wait—this is just hardware.**

**Additional capex components:**
1. **Process development:** $1-5M (qualifying recipes for new nodes)
2. **Chamber maintenance:** $500K-$1M annually (replaceable chamber liners degrade)
3. **Precursor supply & storage:** $200-500K annually (WF₆ requires specialized handling, cryogenic storage)

**Total cost of ownership per wafer (including consumables & service):** $60-100/wafer

**Fab profitability depends on selling wafers for $200-500+/wafer.** Deposition cost is 10-20% of wafer margin.

---

## V. Capital Allocation: Deposition Equipment ROI

**Lam Research deposition segment (2024-2028):**
- **Revenue (estimated):** $8-10B annually
- **Gross margin:** 50-55%
- **Service revenue (recurring):** 40-45% of total
- **Service margin:** 70-75%
- **ROIC:** 38-42% (exceptional for capex-intensive business)

**Why is ROIC so high?**

1. **Installed base moat:** 900+ Ultima™ systems globally, each generating $0.5-1M annual service revenue
2. **Process IP:** Lam controls recipes for each node (22nm, 14nm, 7nm, 5nm, 3nm). Customers cannot switch without 18-24 month re-qualification.
3. **Network effects:** Lam's installed base means fab chooses Lam for new nodes (compatibility with existing recipes)

**Math:**
- One Ultima™ system: $4M capex
- Annual service revenue: $0.75M
- Service gross profit: $0.5M/year
- 7-year IRR on equipment capex: (7 × $0.5M − $4M) / $4M = 87.5% cumulative return = ~12% annual IRR

**But ROIC (operating profit / invested capital) exceeds IRR because:**
- Equipment cost is amortized (not charged upfront)
- Service revenue is pure cash flow after cost of goods sold
- 50%+ gross margin on equipment + 70%+ on service = blended 55%+ gross margin

**Implication:** Lam's ROIC = 38-42% because service revenue compounds without requiring new capex.

---

## VI. The Broader Opportunity

Deposition equipment capex is **$30-50B annually (2024-2028)** across all technologies:

| Technology | Annual Capex | Equipment Vendor Share | Opportunity |
|---|---|---|---|
| CVD (tungsten, copper) | $12-15B | 5% | $600M-750M revenue |
| PVD (barriers, seed) | $5-8B | 5% | $250-400M revenue |
| ALD (high-κ, conformal) | $8-12B | 5% | $400-600M revenue |
| **Total** | **$25-35B** | **~5%** | **$1.25-1.75B opportunity** |

At 50-55% gross margin, deposition equipment vendors capture **$625M-960M in annual gross profit** from the supercycle.

Over 5 years (2024-2028): **$3.1-4.8B cumulative gross profit** from deposition equipment alone.

**This is why Lam Research trades at 15-20x earnings despite being a "mature" company.** The deposition business is in growth mode for the first time since 2015.

---

**Next:** [Chapter 3: Electrodeposition of Copper & Barrier Layers](03-electrodeposition-copper.md)
