# Glossary: Deposition & Materials Engineering Terms

## A

**ALE (Atomic Layer Etch):** Self-limiting etching process that removes one atomic layer per cycle. Used for selective removal of SiGe nanosheets in gate-all-around device preparation.

**ALD (Atomic Layer Deposition):** Deposition method using sequential, self-limiting gas-phase reactions. Each cycle adds ~0.3 nm per atomic layer. Preferred for high-κ dielectrics and conformal coatings.

**Al₂O₃ (Aluminum Oxide):** High-κ dielectric material (κ ≈ 9-10). Used in ALD for conformal barrier layers and interfacial layers.

**AMAT:** Applied Materials; second-largest equipment vendor. Market share: 30-35% deposition equipment.

**ASMPT:** ASM Pacific Technology; flip-chip bumping equipment leader. Equipment: Datapace (solder paste printing, reflow, underfill).

**Arrhenius Equation:** Temperature dependence of reaction rate: k(T) = A × exp(−Ea/RT). Used to model CVD decomposition kinetics.

---

## B

**BDT (Bis-Dithiocarbamate):** Electroplating accelerator additive. Enhances copper deposition in deep trenches; typical concentration 0.5-2 g/L.

**Barrier Layer:** Thin (~2-5 nm) metal or metal-nitride layer deposited before copper plating to prevent copper diffusion into silicon. Materials: tantalum, tungsten.

**Black's Equation:** Electromigration reliability model: MTF ∝ (1/j^n) × exp(Ea/kT). Predicts interconnect lifetime under current stress.

**Breakage Test:** Wafer bonding strength measurement. Bond is fractured mechanically; fracture energy (J/m²) indicates bond quality.

---

## C

**CBO (Conduction Band Offset):** Energy offset between silicon conduction band and dielectric conduction band edge. Critical for gate leakage suppression. Example: SiO₂ CBO ≈ 3.1 eV.

**Chemisorption:** Strong chemical bonding of precursor molecule to surface site. Forms basis of ALD self-limiting reactions.

**Cpk (Process Capability Index):** Statistical measure of process centering and spread. Cpk ≥ 1.33 required for high-yield production.

**Coefficient of Thermal Expansion (CTE):** Material expansion rate with temperature. Si CTE ≈ 2.6 ppm/K; affects warpage and stress.

**CVD (Chemical Vapor Deposition):** Deposition using gas-phase chemical reactions. Requires elevated temperature (300-1000°C). High throughput (~100-200 nm/min).

**Copper Electrodeposition:** Electrochemical plating of copper from CuSO₄ electrolyte. Essential for sub-2nm interconnect via fill.

---

## D

**Dit (Interface Trap Density):** Number of trap states at Si-dielectric interface per unit area per unit energy. Units: cm⁻² eV⁻¹. Lower Dit improves device performance.

**Diffusion Coefficient (D):** Rate of molecular diffusion. Depends on temperature and gas species. Used in transport equations.

**Direct Tunneling:** Quantum mechanical electron transport through energy barrier. Dominant leakage mechanism in thin SiO₂.

---

## E

**Electromigration:** Drift of metal atoms under electric field bias. Major failure mechanism in interconnects. Exponentially dependent on current density and temperature.

**Electroplating:** Deposition of metal via electrochemistry (electrical current provides energy). Used for copper via fill at sub-2nm nodes.

**EOT (Equivalent Oxide Thickness):** SiO₂ equivalent thickness of high-κ dielectric stack. Used to compare capacitance scaling. Formula: EOT = t_hk / κ_rel.

**Etching:** Removal of material using chemical or plasma energy. Complementary process to deposition.

---

## F

**Faraday Constant (F):** Charge of one mole of electrons: 96,485 C/mol. Used in electroplating rate calculations.

**Fluorine Chemistry:** Precursor chemistry using fluorine-containing compounds (WF₆, SiF₄, etc.). Common in CVD; requires careful HF byproduct handling.

---

## G

**GAA (Gate-All-Around):** Transistor gate geometry where gate wraps around channel on all sides. Requires conformal high-κ dielectrics (ALD-only).

**Grain Boundary:** Interface between crystalline grains in polycrystalline material. Trap sites for carriers; degrades performance.

---

## H

**HfO₂ (Hafnium Oxide):** High-κ dielectric material (κ ≈ 20-25). Preferred for sub-3nm gate dielectrics due to bandgap, CBO, and thermal stability.

**High-κ Dielectric:** Dielectric material with permittivity > 10 (vs. SiO₂ κ ≈ 3.9). Enables thicker films while maintaining same capacitance, reducing leakage.

**Hydrogen Evolution:** Side reaction in electroplating producing H₂ gas. Creates void nucleation sites; must be suppressed via additives.

---

## I

**Ion Implantation:** Dopant introduction via high-energy ion bombardment. Complementary process to deposition.

**Ionized PVD:** Advanced sputtering technique ionizing sputtered atoms after leaving target. Improves step coverage in high-aspect-ratio trenches.

**IR (Infrared) Monitoring:** Real-time measurement of wafer temperature during processing. Used for thermal feedback control in CVD/ALD.

---

## J

**JEDEC:** Joint Electron Device Engineering Council. Standards body for semiconductor specifications (wafer bonding, thermal cycling, etc.).

---

## K

**K&S (Kulicke & Soffa):** Wire bonding equipment manufacturer. Legacy technology; declining market share; focused on mature nodes.

---

## L

**Lam Research:** Largest deposition equipment vendor. Market share: 40-45% (CVD, ALD, electroplating). ROIC: 38-42%.

**Langmuir Isotherm:** Adsorption model describing monolayer formation: θ(t) = θ_sat × [1 − exp(−t/τ)]. Applied to ALD saturation kinetics.

**LRCX:** Lam Research stock ticker.

---

## M

**Magnetron Sputtering:** PVD technique using magnetic field to enhance ionization. Improves deposition rate and film quality.

**Mean Free Path (λ):** Average distance gas molecule travels before collision. In PVD, must be >> chamber size for ballistic transport.

**Monolayer:** Single atomic layer of material. ALD deposits ~0.3 nm per cycle (~1 monolayer).

**MTTF (Mean Time To Failure):** Average lifetime before failure. Used to predict electromigration reliability.

---

## N

**Nucleation:** Initial formation of solid phase from precursor. Critical for void-free copper plating.

---

## O

**Overpotential (η):** Deviation of applied potential from equilibrium potential. Determines electrochemistry reaction rate and byproduct formation.

**Oxygen Vacancy:** Missing oxygen atom in dielectric lattice (e.g., HfO₂₋ₓ). Creates trap sites; cause of TDDB failures.

---

## P

**PEG (Polyethylene Glycol):** Electroplating suppressor additive. Inhibits copper deposition; promotes leveling. Typical concentration: 10-20 g/L.

**PVD (Physical Vapor Deposition):** Deposition using ballistic material transport (no chemical reactions). Room-temperature capable; excellent adhesion. Slow deposition (~10-20 nm/min).

**Post-Deposition Annealing (PDA):** Thermal treatment after deposition. Used to crystallize dielectrics, reduce oxygen vacancies, improve reliability.

**Precursor:** Gas-phase chemical used in CVD or ALD. Examples: WF₆ (tungsten), TDMAH (hafnium), silane (silicon).

**Purge:** Inert gas pulse used in ALD to remove excess precursor before co-reactant pulse. Essential for preventing CVD-like reactions.

---

## Q

**Qualification:** Testing and validation process when introducing new equipment or recipes to production. Typical duration: 6-12 months per new node.

---

## R

**Reaction Order:** Exponent describing concentration dependence of reaction rate. r = k[A]^n; n is order.

**Resistivity (ρ):** Measure of electrical resistance per unit length. Higher ρ increases interconnect delay. Example: Ta ρ ≈ 1,000-2,000 μΩ-cm.

**ROIC (Return on Invested Capital):** Operating profit divided by invested capital. Measures capital efficiency. Target for equipment vendors: 30-40%.

---

## S

**Saturation (Precursor):** Maximum surface coverage of precursor molecules. Self-limiting ALD reactions depend on complete saturation.

**Sputtering Yield:** Number of target atoms ejected per incident ion. Depends on ion energy and target material. Typical: 0.5-2 atoms/ion.

**Standard Cubic Centimeters per Minute (sccm):** Volumetric flow rate unit for gases. 1 sccm = 1 cm³/min at standard pressure (760 Torr) and temperature (273 K).

**Substrate Bias:** Negative voltage applied to substrate during sputtering. Accelerates ions toward substrate; improves film quality and adhesion.

---

## T

**Ta (Tantalum):** Barrier layer material. Higher conductivity than tungsten; preferred for ultra-thin barriers. Density ≈ 16.65 g/cm³.

**TDMAH (Tetrakis(Dimethylamino)Hafnium):** Hafnium precursor for ALD. Pyrophoric; requires careful handling. Boiling point ≈ 160°C.

**TEL (Tokyo Electron):** Japanese deposition equipment vendor. Market share: 15-20% (strong in Asia).

**TEM (Transmission Electron Microscopy):** High-resolution imaging technique used to verify film thickness, uniformity, and defects.

**Thermal Interface Material (TIM):** Material for thermal management between chip and heat sink. Thermal conductivity κ ≈ 50-80 W/m·K for liquid metal.

**TDDB (Time-Dependent Dielectric Breakdown):** Gradual degradation of dielectric under electric field bias. Failure mechanism for gate dielectrics.

**Through-Silicon Via (TSV):** Vertical copper via connecting multiple die layers in 3D NAND or chiplets.

**Torch Measurement:** In-situ optical measurement of substrate temperature during CVD/ALD processing.

**Tunneling Current:** Quantum mechanical electron transport through energy barrier. Dominant leakage for thin SiO₂ at high voltages.

---

## U

**UCIe (Universal Chiplet Interconnect Express):** Standard chiplet interconnect protocol. Competes with EMIB (Intel's proprietary standard).

**Ultrapure Water:** High-purity deionized water (<1 ppb impurities). Required for ALD co-reactant to prevent contamination.

---

## V

**VBO (Valence Band Offset):** Energy offset between silicon valence band and dielectric valence band edge. Example: SiO₂ VBO ≈ 4.5 eV.

**Void:** Empty space inside via or interconnect. Caused by incomplete plating or hydrogen bubble entrapment. Major failure mode.

---

## W

**Wafer Bonding:** Direct adhesion of two wafers through dielectric, metal, or hybrid interfaces. Used in 3D NAND, chiplet integration, and wafer-level packaging.

**Warpage:** Bowing of wafer due to stress from thermal processing or material properties mismatch. Typical: 50-200 μm for 300mm wafers.

**WF₆ (Tungsten Hexafluoride):** Tungsten precursor for CVD. Gas phase at room temperature; highly reactive. Byproduct HF is corrosive.

**Window (Process):** Range of processing parameters (temperature, pressure, flow rate) that produce acceptable results. Wider window = more robust process.

---

## X

**X-ray Diffraction (XRD):** Crystallography technique measuring crystal phase and grain size. Used to characterize dielectric films.

---

## Y

**Yield:** Percentage of wafers or dies that meet specifications after processing. Improved by tighter process capability (higher Cpk).

**Young's Modulus:** Material stiffness under applied stress. Si ≈ 130 GPa; affects warpage and stress engineering.

---

## Z

**Zero-Defect Manufacturing:** Target of defect-free wafer production. Practically: <10 ppm defect rate (Cpk > 2.0).

---

## Acronyms & Abbreviations

| Acronym | Definition |
|---|---|
| **ALE** | Atomic Layer Etch |
| **ALD** | Atomic Layer Deposition |
| **AMAT** | Applied Materials |
| **ASMPT** | ASM Pacific Technology |
| **CBO** | Conduction Band Offset |
| **CVD** | Chemical Vapor Deposition |
| **CTE** | Coefficient of Thermal Expansion |
| **Dit** | Interface Trap Density |
| **EOT** | Equivalent Oxide Thickness |
| **GAA** | Gate-All-Around |
| **HfO₂** | Hafnium Oxide |
| **IL** | Interfacial Layer |
| **JEDEC** | Joint Electron Device Engineering Council |
| **K&S** | Kulicke & Soffa |
| **LRCX** | Lam Research (ticker) |
| **MTBF** | Mean Time Between Failure |
| **MTTF** | Mean Time To Failure |
| **PDA** | Post-Deposition Annealing |
| **PEG** | Polyethylene Glycol |
| **PVD** | Physical Vapor Deposition |
| **ROIC** | Return on Invested Capital |
| **sccm** | Standard Cubic Centimeters per Minute |
| **Ta** | Tantalum |
| **TDMAH** | Tetrakis(Dimethylamino)Hafnium |
| **TDDB** | Time-Dependent Dielectric Breakdown |
| **TEL** | Tokyo Electron |
| **TEM** | Transmission Electron Microscopy |
| **TIM** | Thermal Interface Material |
| **TSV** | Through-Silicon Via |
| **UCIe** | Universal Chiplet Interconnect Express |
| **VBO** | Valence Band Offset |
| **W** | Tungsten |
| **WF₆** | Tungsten Hexafluoride |
| **XRD** | X-ray Diffraction |

---

**End of Glossary**

See other appendices for mathematical derivations, equipment specifications, and knowledge-base cross-references.
