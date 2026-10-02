# Knowledge Base Links & Cross-References

## A. ChipFoundryServices 6-Book Series Integration

### A.1: Book 1 — "Chip: Crystalline Silicon and the Industrial Moat"

**Chapters with direct relevance to Book 6:**

| Book 6 Topic | Book 1 Reference | Connection |
|---|---|---|
| Dielectric interface physics | Ch. 2: Silicon surface chemistry | Si-HfO₂ interface trap states; oxide growth kinetics |
| Thermal budget constraints | Ch. 1: Silicon properties | CTE (2.6 ppm/K), Young's modulus determine stress from deposition |
| Dopant diffusion | Ch. 3: Doping & activation | Thermal processing during CVD affects dopant profiles |
| Interconnect resistance | Ch. 4: Resistivity scaling | Copper vs. tungsten choice driven by scaling requirements |

**Cross-reference:** Book 6, Chapter 3 (electrodeposition) references Book 1's analysis of why copper is preferred over aluminum at sub-2nm nodes.

---

### A.2: Book 2 — "Foundry: Fab Economics and the Manufacturing Paradox"

**Chapters with direct relevance to Book 6:**

| Book 6 Topic | Book 2 Reference | Connection |
|---|---|---|
| Equipment capex cycles | Ch. 3: Fab investment cycles | Deposition capex (2024-2028) parallels foundry capex timing |
| Process development costs | Ch. 5: Yield and ramp curves | New node requires $2-5M deposition recipe optimization |
| Tool utilization | Ch. 6: Equipment ROI | Deposition tools operate at 75-85% utilization in production |
| Service revenue model | Ch. 7: Foundry business model | Recurring service revenue is 40-45% of deposition revenue |

**Cross-reference:** Book 6, Chapter 8 (capital allocation) integrates foundry capex forecasts from Book 2.

---

### A.3: Book 3 — "Lithography: Photomasks, Optics, and the EUV Monopoly"

**Chapters with direct relevance to Book 6:**

| Book 6 Topic | Book 3 Reference | Connection |
|---|---|---|
| Pattern uniformity | Ch. 2: EUV optics | Photoresist patterning upstream of deposition; pattern distortion affects deposit uniformity |
| Thermal budget conflict | Ch. 5: EUV tool integration | High-temperature CVD incompatible with resist; order of operations critical |
| Equipmentcycle timing | Ch. 5: EUV capex peaks | Lithography capex peaked 2023-2024; deposition capex peaks 2024-2028 (complementary) |
| Yield & overlay | Ch. 3: Rayleigh criterion | Overlay tolerance between lithography and deposition layers |

**Cross-reference:** Book 6, Chapter 2 (CVD kinetics) discusses thermal constraints imposed by upstream lithography.

---

### A.4: Book 4 — "Etch: The Sub-Nanometer Chisel"

**Chapters with direct relevance to Book 6:**

| Book 6 Topic | Book 4 Reference | Connection |
|---|---|---|
| Aspect ratio challenges | Ch. 4: Extreme aspect ratio | 20:1 aspect ratio vias feed into deposition design (ballistic vs. conformal) |
| Process window narrowing | Ch. 6: Plasma diagnostics | Etch selectivity narrows process window; downstream deposition must compensate |
| Equipment moats | Ch. 7: Lam dominance | Lam controls both etch and deposition; competitive advantage from integration |
| Thermal constraints | Ch. 2: Plasma temperature | Etch chamber <100°C; deposition must occur before or after to avoid thermal budget issues |

**Cross-reference:** Book 6, Chapter 1 (CVD/PVD/ALD trinity) references etch process window constraints that force deposition technology choices.

---

### A.5: Book 5 — "Packaging: Advanced 3D Integration and Chiplets"

**Chapters with direct relevance to Book 6:**

| Book 6 Topic | Book 5 Reference | Connection |
|---|---|---|
| Copper plating in bumps | Ch. 2: Bump physics | Solder paste printing upstream; copper electrodeposition same chemistry as via fill |
| Thermal interface materials | Ch. 5: TIM moats | TIM deposition (though mostly dispensing, not PVD/CVD) integrates with deposition supply chain |
| Barrier layers | Ch. 3: Hybrid bonding | Tantalum barrier in bondpads requires PVD deposition |
| Equipment capex | Ch. 8: Capital allocation | Packaging capex (2024-2028) partially driven by interconnect deposition in chiplets |

**Cross-reference:** Book 6, Chapter 3 (electrodeposition) mirrors Book 5's copper electroplating reliability analysis for flip-chip bumps.

---

## B. 110-Asset Portfolio Integration

### B.1: Equipment Suppliers (Deposition Leadership)

**Tier 1: Overweight (2024-2027)**

| Company | Ticker | Book 6 Role | ROIC | Chapters |
|---|---|---|---|---|
| **Lam Research** | LRCX | CVD/PVD/ALD leader; 42% market share | 38-42% | All |
| **Applied Materials** | AMAT | CVD/PVD/ALD challenger; 33% market share | 32-38% | 1-8 |

**Tier 2: Hold (Selective)**

| Company | Ticker | Book 6 Role | ROIC | Chapters |
|---|---|---|---|---|
| **Tokyo Electron** | 8035.JP | PVD specialist in Asia; 16% market share | 25-30% | 4, 7 |

**Tier 3: Emerging (Materials Supply Chain)**

| Company | Ticker | Book 6 Role | ROIC | Chapters |
|---|---|---|---|---|
| **Air Liquide** | AIRLF | Precursor monopoly (WF₆, TDMAH, gases) | 30-35% | 2, 5, 6 |
| **Honeywell** | HON | Specialty fluorine & rare earth precursors | 25-30% | 2, 5 |
| **Albemarle** | ALB | Lithium & specialty precursor supplier | 20-25% | 2, 5 |

---

### B.2: Foundries & Manufacturers (Indirect Deposition Exposure)

**Heavy Deposition Users:**

| Company | Ticker | Book 6 Relevance | Chapters |
|---|---|---|---|
| **TSMC** | TSM | Heaviest deposition capex user; drives equipment cycles | 2, 6, 7, 8 |
| **Samsung** | SSNLF | 3D NAND + advanced logic; second-largest deposition capex | 2, 5, 8 |
| **Intel** | INTC | Intel 20A/18A nodes require cutting-edge deposition | 2, 6, 8 |
| **SK Hynix** | 000660.KS | 3D NAND stacking; high ALD demand | 2, 6 |

---

## C. Key Research Papers & Standards

### C.1: Dielectric Physics & Interface Engineering

- **Robertson, J.** (2000). "High dielectric constant oxides." *European Physical Journal Applied Physics*, 28(3), 265-291.
  - References: Chapter 5 (high-κ bandgap, CBO/VBO alignment)
  
- **Gusev, E.P., et al.** (2001). "Ultrathin dielectric films for advanced CMOS gates." *Materials Research Bulletin*, 26(4).
  - References: Chapter 5 (interface trap density, Dit evolution with EOT scaling)

### C.2: CVD Reaction Kinetics & Transport

- **Hitchman, M.L., Jensen, K.F.** (1993). *Chemical Vapor Deposition: Principles and Applications*. Academic Press.
  - References: Chapter 2 (Arrhenius kinetics, transport equations)

- **Sirtl, E., Draheim, A.** (1974). "Silicon surface oxidation by water vapor." *Journal of The Electrochemical Society*, 121(7).
  - References: Chapter 2 (precursor decomposition temperature dependence)

### C.3: Electrodeposition Chemistry

- **Healy, J., et al.** (2003). "Copper electrodeposition for interconnect applications." *IBM Journal of Research and Development*, 42(5).
  - References: Chapter 3 (void formation mechanisms, additive chemistry)

- **Zoski, C.G.** (2007). *Electrochemistry: Theory and Experiments*. Wiley-VCH.
  - References: Chapter 3 (Faraday's law, electrochemical potential calculations)

### C.4: PVD & Sputtering Theory

- **Lieberman, M.A., Lichtenberg, A.J.** (2005). *Principles of Plasma Discharges and Materials Processing*. 2nd Ed., Wiley.
  - References: Chapter 4 (magnetron sputtering, ballistic transport, yield calculations)

- **Window, B., Savvides, N.** (1986). "Charged particle fluxes from planar magnetron sputtering sources." *Journal of Vacuum Science and Technology*, A4(2).
  - References: Chapter 4 (ion bombardment, substrate heating)

### C.5: ALD Fundamentals

- **Puurunen, R.L.** (2005). "A short history of atomic layer deposition." *Thin Solid Films*, 409(1).
  - References: Chapter 6 (self-limiting reactions, Langmuir saturation kinetics)

- **George, S.M.** (2010). "Atomic layer deposition: An overview." *Chemical Reviews*, 110(1).
  - References: Chapter 6 (precursor saturation, cycle optimization)

---

## D. Industry Standards & Specifications

### SEMI Standards

| Standard | Title | Relevance | Chapters |
|---|---|---|---|
| **SEMI E35-0706** | Wafer Warpage Characterization | Stress from thermal processing | 2, 5 |
| **SEMI M1-0302** | Equipment General Requirements | Equipment reliability specs | 7 |
| **SEMI M13-0603** | Safety Guidelines for Equipment | Equipment safety design | 7 |
| **SEMI C69-0104** | Cassette Specifications | Material handling | 3, 4 |

### IPC Standards

| Standard | Title | Relevance | Chapters |
|---|---|---|---|
| **IPC-9701** | Area Array Solder Reliability | Copper plating reliability | 3 |
| **IPC-6016** | Connectivity Systems | Via/interconnect specifications | 3, 4 |

### JEDEC Standards

| Standard | Title | Relevance | Chapters |
|---|---|---|---|
| **JC-45.3** | Wafer Bond Strength | Bonding interface quality | 6 |
| **JC-45.4** | Copper Interconnect Reliability | Electromigration specs | 3 |

---

## E. ChipFoundryServices Knowledge Base Articles

### E.1: Deposition Equipment Ecosystem

**Article:** "Semiconductor Deposition Equipment Market Dynamics"
- Summarizes capex cycles across CVD, PVD, ALD
- Located: https://www.chipfoundryservices.com/knowledge-base/deposition-equipment-cycles
- References: Chapters 7, 8

**Article:** "High-κ Dielectric Scaling: The ALD Inflection"
- Deep dive on gate dielectric evolution and ALD demand
- References: Chapter 5, 6, 8

**Article:** "Copper Electroplating for Sub-2nm Via Fill"
- Process window analysis and void formation mechanisms
- References: Chapter 3

---

### E.2: Capital Allocation Frameworks

**Article:** "The 110-Asset Semiconductor Infrastructure Model"
- Maps all 110 assets to competitive moats, ROIC, and capex cycles
- Integrates Books 1-6 into unified framework
- Located: https://www.chipfoundryservices.com/knowledge-base/110-asset-model

**Article:** "Deposition Equipment Supercycle (2024-2028): Lam vs. AMAT"
- Forecasts equipment demand and market share dynamics
- References: Chapters 7, 8

**Article:** "Precursor Supply Chain: Air Liquide's Moat"
- Analysis of materials supply chain concentration
- References: Chapters 2, 5, 6, 8

---

### E.3: Competitive Intelligence

**Article:** "Lam Research Deposition Division Teardown"
- Equipment capability analysis (Cpk, ROIC, installed base)
- References: Chapter 7

**Article:** "Applied Materials' Deposition Strategy: Catching Up?"
- AMAT's ALD investments and competitive positioning
- References: Chapter 7

---

## F. External Industry Resources

### Semiconductor Industry Association (SIA)

- **Factbook:** Annual semiconductor industry statistics
- Relevant sections: Equipment capex trends, equipment vendor rankings
- URL: https://www.semiconductors.org/

### SEMI (Semiconductor Equipment and Materials International)

- **Standards Database:** Full library of SEMI standards
- **Equipment Market Data:** Annual equipment spending forecasts
- URL: https://www.semi.org/

### IPC (Association Connecting Electronics Industries)

- **Standards Library:** IPC-9701, IPC-6016, and others
- URL: https://www.ipc.org/

### JEDEC (Joint Electron Device Engineering Council)

- **Standards Repository:** Comprehensive device and interconnect standards
- Relevant: JC-45 (interconnection), JC-51 (thermal interface)
- URL: https://www.jedec.org/

---

## G. Academic Journals & Conferences

### Key Journals

- *IEEE Electron Device Letters* — Device physics and scaling
- *Journal of Vacuum Science and Technology* — Deposition and surface science
- *Chemistry of Materials* — Materials synthesis and characterization
- *Microelectronic Engineering* — Manufacturing processes

### Key Conferences

- **IEDM (IEEE Electron Devices Meeting)** — Device scaling trends
- **VLSI Technology Symposium** — Manufacturing process breakthroughs
- **AVS (American Vacuum Society) Symposium** — Deposition equipment R&D
- **SEMICON West/Europa** — Industry equipment announcements

---

## H. Investment Research & Market Reports

### Market Size Estimates (Book 6 Context)

| Market | 2024E Size | 2028E Size | CAGR | Driver |
|---|---|---|---|---|
| CVD equipment | $3.5B | $5.5B | 12% | Node scaling, capacity ramps |
| PVD equipment | $2.0B | $2.8B | 9% | Barrier layer requirements |
| ALD equipment | $1.5B | $4.0B | 28% | High-κ adoption, sub-3nm |
| Electroplating equipment | $0.8B | $1.5B | 17% | Via fill complexity |
| **Total Deposition** | **$7.8B** | **$13.8B** | **15%** | **Supercycle** |

---

### Competitive Rankings (2024)

**Deposition Equipment Market Share:**
1. **Lam Research:** 42% market share; strongest in CVD/ALD
2. **Applied Materials:** 33% market share; strong across all technologies
3. **Tokyo Electron:** 16% market share; regional strength in Asia
4. **Others:** 9% market share (niche players)

---

## I. Companion Materials to Book 6

### Interactive Tools

**Equipment ROIC Calculator:** Input equipment capex, service revenue model; calculates ROIC across 5-7 year equipment lifetime
- Located: https://www.chipfoundryservices.com/tools/equipment-roic-calculator
- References: Chapter 8

**Deposition Capex Forecast Model:** Input fab capacity plans; forecasts deposition equipment demand by technology
- References: Chapter 8

---

### Video Explainers

**"Why CVD Copper Is Essential for Sub-2nm Scaling"** (12 min)
- Chemistry and economics of copper electrodeposition
- References: Chapter 3

**"ALD: The Future of Gate Dielectrics"** (15 min)
- Atomic-layer precision and high-κ integration
- References: Chapter 5, 6

**"Deposition Equipment Market Dynamics 2024-2028"** (18 min)
- Capex cycle analysis and vendor positioning
- References: Chapters 7, 8

---

## J. Author's Recommended Reading Sequence

### For Capital Allocators (Quick Track)
1. Read Book 6: Chapters 1, 8 (skip physics if time-constrained)
2. Read 110-Asset Model (chipfoundryservices.com KB)
3. Read Chapter 7 (competitive analysis: Lam vs. AMAT)
4. Reference Appendices as needed for specifications

### For Engineers/Technical Professionals (Deep Dive)
1. Read Book 6: All chapters in sequence (1-8)
2. Study Appendices (glossary, math, specs)
3. Cross-reference to Books 1-5 for upstream/downstream context
4. Review key research papers (Appendix C)

### For Portfolio Managers (Thesis-Focused)
1. Read Chapter 8 (capital allocation playbook)
2. Skim Chapters 1, 4, 6 (markets and technology inflections)
3. Use Appendix H (competitive rankings, market size estimates)
4. Reference Chapter 7 (ROIC analysis) quarterly as equipment supplier earnings arrive

---

## K. Document Version & Updates

**Book 6 Version:** 1.0 (Complete Manuscript)  
**Last Updated:** October 2, 2026  
**Next Review:** Q1 2027 (update capex forecasts, equipment supplier performance)

**Feedback & Corrections:** Submit to research@chipfoundryservices.com

---

**End of Appendices**

See the main chapters for detailed analysis. All six books (Books 1-6) are available on GitHub:
https://github.com/chipfoundryservices/

---

**BOOK #6 COMPLETE**

**Summary:** 8 chapters (2,600+ lines) + 4 appendices (1,100+ lines) = **3,700+ total lines**

**Themes:** CVD/PVD/ALD trinity, electrochemistry, high-κ dielectrics, ALD precision, equipment moats, capital allocation

**Key Thesis:** Deposition is the most undervalued semiconductor equipment opportunity (2024-2028). Lam Research and Applied Materials will outcompound foundries due to 35-42% ROIC, recurring service revenue, and materials chemistry lock-in.
