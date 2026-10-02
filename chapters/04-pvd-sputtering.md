# Chapter 4: PVD & Sputtering: Ballistic Material Transport

## The Room-Temperature Requirement

CVD and electroplating work great for tungsten vias and copper interconnects. But they fail for **barrier layers.**

Why? Because barrier layers (tantalum, tungsten) must be deposited **at room temperature or below,** before copper plating. Any thermal processing would degrade the underlying dielectric or gate stack.

Electroplating cannot deposit tantalum (not easily electrochemically reduced). CVD requires 300-600°C (too hot).

**Only PVD works at room temperature.**

This chapter reveals why barrier layer deposition is the equipment bottleneck at sub-3nm nodes, and why PVD equipment vendors command 25-35% ROIC despite lower prices than CVD tools.

---

## I. Inversion: The PVD Failures

### Failure 1: Step Coverage Loss in Deep Trenches

PVD atoms travel in straight lines from target to substrate (ballistic transport).

**Consequence:** In a high-aspect-ratio trench (20:1 aspect ratio = 500 nm deep, 25 nm wide):
- Top of trench: Exposed to target; receives full flux
- Middle of trench: Receives flux at oblique angle; reduced flux
- Bottom of trench: Shaded from target; receives almost no flux

**Coverage variation:**
- Top thickness: 10 nm
- Middle thickness: 5 nm
- Bottom thickness: 2 nm

**Catastrophe:** Barrier layer at trench bottom is 5 nm, but should be 3 nm for optimal properties. If bottom is thinner than 2 nm, **copper diffuses through under operating temperature.**

### Failure 2: Contamination from Target Impurities

Tantalum target contains trace impurities:
- Oxygen (0.1-0.5%)
- Carbon (0.01-0.1%)
- Tungsten (residual from prior processes)

When sputtering, **all impurities are sputtered along with tantalum.**

**Consequence:**
- Oxygen in barrier → forms tantalum oxide (Ta₂O₅) → higher resistivity
- Carbon in barrier → forms tungsten carbide precipitates → brittleness
- Tungsten in tantalum barrier → increases resistivity

**Impact:** Barrier resistivity increases 20-40%, increasing interconnect RC time delay.

### Failure 3: Substrate Temperature Rise

Ion bombardment during sputtering heats the substrate.

**Mechanism:**
- Sputtered atoms arrive with kinetic energy (~10-100 eV)
- Upon impact, kinetic energy converts to heat
- Temperature rise: ±20-50°C above ambient

**Consequence:** At 50°C substrate temperature (due to ion bombardment):
- Resist (photoresist used for patterning) may soften
- Dielectric properties degrade
- Outgassing from underlying layers occurs

**Solution:** Active substrate cooling (helium backside cooling) required.

### Failure 4: Film Texture & Grain Growth

PVD-deposited tantalum has very fine grain structure initially (~10-20 nm grains).

But under subsequent thermal stress (e.g., during copper plating at room temperature), grains grow to ~50-100 nm, **doubling resistivity.**

**Catastrophe:** Measured initially: barrier resistivity = 100 μΩ-cm. After copper plating: 200 μΩ-cm. Interconnect performance degrades.

---

## II. Physics: Sputtering Yield & Ballistic Transport

### A. Sputtering Mechanism

**Three-step process:**

1. **Ion generation:** Inert gas (Ar) ionized by electric field
   ```
   Ar + e⁻ → Ar⁺ + 2e⁻   (impact ionization)
   ```

2. **Ion acceleration:** Ar⁺ accelerated toward negatively biased target (−500V to −2000V)
   ```
   Ar⁺ kinetic energy = e × |V_target| = e × |−800V| = 800 eV (typical)
   ```

3. **Target collision & sputtering:** Ar⁺ hits target, knocking off target atoms
   ```
   Ar⁺ + Ta → Ar (neutralized) + Ta (ejected)
   ```

### B. Sputtering Yield

**Sputtering yield Y** = number of target atoms ejected per incident ion.

**Dependence on target material and ion energy:**

For Ar⁺ sputtering tantalum at 800 eV:
```
Y ≈ (α × E) / (U_d + E/3)
```

Where:
- α = constant (~0.2 for Ar-Ta)
- E = ion energy (eV)
- U_d = displacement energy (~40 eV for Ta)

**Numerical example:**
- E = 800 eV
- Y ≈ (0.2 × 800) / (40 + 800/3) ≈ 160 / 310 ≈ **0.5 atoms/ion**

**Consequence:** At 10 mA/cm² current density, sputter rate is ~10 nm/min.

**Comparison to CVD:** CVD deposits ~100-200 nm/min; PVD is 10-20x slower.

---

### C. Ballistic Transport in Vacuum

**Key assumption:** Sputtered atoms travel through vacuum without collisions.

**Mean free path:**
```
λ = 1 / (n_gas × σ)
```

Where:
- n_gas = gas molecule density
- σ = collision cross-section (~10⁻¹⁶ cm²)

At typical PVD pressures (1-10 mTorr):
- n_gas ≈ 10¹⁴ molecules/cm³
- λ ≈ 10 cm (much larger than chamber size ~30 cm)

**Consequence:** Sputtered atoms travel in straight lines; no diffuse scattering.

### D. Deposition Rate as Function of Aspect Ratio

**Angular distribution of sputtered atoms:**

Sputtered atoms are ejected at various angles (not purely normal to target). Angular distribution follows:
```
dY/dθ ∝ cos^n(θ)
```

Where θ = angle from normal, n ≈ 2-3.

**For a high-aspect-ratio trench:**

Atoms ejected at oblique angles (θ = 60°) deposit only cos²(60°) = 25% of normal flux.

**Thickness at trench bottom** (accounting for shadowing):
```
t_bottom / t_top ≈ cos(α)
```

Where α = trench aspect angle.

For 20:1 aspect ratio trench: α ≈ 87°, cos(87°) ≈ 0.05 → **95% thickness loss at bottom!**

**Practical consequence:** PVD alone cannot fill deep trenches. Must use **collimation** (angled deposition from multiple angles) or **ionized PVD** (plasma-enhanced sputtering).

---

## III. Practice: Equipment Design & Magnetron Sputtering

### Magnetron Sputtering

**Advanced PVD technique:** Magnetic field confines electrons near target, increasing ionization efficiency.

**Components:**
1. **Target:** Tantalum (or tungsten) disk, negatively biased (−800V)
2. **Cathode sheath:** Thin plasma zone near target where Ar⁺ ions are accelerated
3. **Anode:** Substrate holder (grounded or at small positive potential)
4. **Magnetic field:** Permanent magnets behind target, creating B-field ~0.1-0.5 Tesla

**Electron confinement:** Magnetic field curves electron trajectories, trapping them near target surface. This increases ionization rate (more Ar⁺ produced), increasing sputter rate.

### Deposition Rate & Pressure Control

**Deposition rate dependence on pressure:**

| Pressure (mTorr) | Deposition Rate (nm/min) | Sputtering Yield |
|---|---|---|
| 1 | 5-8 | High (long mean free path) |
| 5 | 8-12 | Optimal |
| 10 | 10-15 | Good (still ballistic) |
| 20 | 8-10 | Degrading (collisions occurring) |

**Trade-off:** Higher pressure increases deposition rate but increases collisions and reduces ballistic transport quality.

**Optimal pressure:** 5-10 mTorr (balance between rate and film quality).

### Ionized PVD (for step coverage)

**Advanced technique:** Ionize sputtered atoms after leaving target.

**Process:**
1. Sputter tantalum normally (ballistic)
2. Ionize a fraction of sputtered Ta atoms using secondary plasma
3. Apply negative bias to substrate; ionized Ta atoms are accelerated toward substrate
4. Ions follow E-field lines, reaching trench bottom preferentially

**Consequence:** Step coverage improves from 20% (normal PVD) to 80%+ (ionized PVD).

**Trade-off:** Substrate heating increases; requires cooling capability.

---

## IV. Economics: Why PVD Is Slow But Necessary

### Market Size & Equipment Cost

**PVD market (2024-2028):**
- TAM: $5-8B annually in fab capex for barrier/seed layers
- Equipment vendor share: ~5% = $250-400M equipment revenue
- Average system cost: $2-3M

**Why lower price than CVD?**
- Simpler pressure control (no CVD byproduct scrubbing needed)
- No precursor supply chain management
- Lower process development cost (more established recipes)

### Service Revenue & ROIC

**Per PVD system:**
- Equipment capex: $2.5M
- Annual throughput: ~5,000 wafers/year (slower than CVD)
- Service cost per system: $200-300K/year

**Service revenue breakdown:**
- Maintenance: $80-100K/year
- Consumables (target replacement): $80-120K/year
- **Service gross margin:** 60-65%
- **Service gross profit/year:** $120-150K

**7-year cumulative:**
- Equipment gross profit: $400K (16% margin on $2.5M)
- Service gross profit: $840K (7 × $120K)
- **Total gross profit: $1.24M on $2.5M capex = 50% gross return**
- **ROIC: 20-25% (lower than CVD 38-42%)**

---

## V. Target Materials & Resistance

### Tantalum Target Properties

| Property | Specification | Impact |
|---|---|---|
| **Purity** | >99.95% | Impurities increase barrier resistivity |
| **Density** | 16.65 g/cm³ | Atomic arrangement affects sputtering yield |
| **Grain structure** | Fine-grained (<10 μm) | Coarse grains → non-uniform sputtering |
| **Cost** | $500-1,000/kg | Not major cost driver |

### Barrier Layer Properties (Tantalum)

| Property | Specification | Target Value |
|---|---|---|
| **Thickness** | 2-5 nm | Thinner is better (lower resistivity), but must prevent Cu diffusion |
| **Resistivity** | ρ | 100-150 μΩ-cm (ultrathin layers have higher ρ due to grain boundary scattering) |
| **Uniformity** | Edge-to-center | ±10% (driven by angular distribution of sputtered atoms) |
| **Adhesion** | Critical | Must bond firmly to SiO₂ and to copper |

---

## VI. Capital Allocation: PVD as Infrastructure Bottleneck

### Why PVD Equipment Is Undervalued

Most semiconductor analysts focus on lithography (ASML) or CVD (Lam). PVD is viewed as "mature" and "low-growth."

**This is wrong.** At sub-3nm nodes:
1. **Barrier layers are thinner:** 2-5 nm barrier requires better uniformity control → demands new PVD equipment
2. **Ionized PVD adoption:** 80%+ fab adoption by 2027 → capital cycle beginning now
3. **Process IP:** Each new node requires new target materials, ionization recipes → suppliers earn recurring revenue

### Equipment Vendor Opportunity

**Lam Research, Applied Materials, Tokyo Electron** (combined market share: 70%+) face PVD capex cycle:

**Forecast (2024-2028):**
- Annual PVD capex: $5-8B across all fabs
- Equipment vendors' share: 5% = $250-400M/year
- Gross profit at 50%+ margin: $125-200M/year
- **5-year cumulative: $625M-$1B**

**Why is this valuable?**
1. Recurring service revenue (targets, maintenance)
2. Process IP (ionized PVD recipes) creates 18-24 month lock-in for customers
3. Installed base network effects (fabs want compatible equipment)

---

## VII. Alternative: Electroless Plating

**Emerging technology:** Deposit tantalum without electrical current (electroless plating).

**Mechanism:** Chemical reduction of tantalum salts using reducing agents (e.g., dimethylamine borane).

**Advantages:**
- No current control required → simpler process
- Excellent step coverage (chemical, not ballistic) → fills trenches perfectly
- Room temperature

**Disadvantages:**
- Slower deposition (1-5 nm/min vs. 10 nm/min for sputtering)
- Requires specialized chemistry + precursor supply
- Still emerging; only 2-3 suppliers globally
- Adoption timeline: 2027+ (not yet mainstream)

**Capital allocation:** Electroless plating vendors (if they exist or emerge) could capture 5-10% of barrier layer market by 2030.

---

**Next:** [Chapter 5: High-κ Dielectrics & Gate Stack Engineering](05-high-k-dielectrics.md)
