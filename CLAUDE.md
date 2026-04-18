# ROG-Estimator — Benign Gynecologic Growth Rate Estimator

## Project Overview
Evidence-based web calculator for estimating growth patterns of benign gynecologic masses. Pure client-side HTML/CSS/JS — no build system, no dependencies.

## File Structure
```
index.html   — Main page structure, form layout, results display containers
script.js    — All calculation logic, form handling, dynamic inputs, references (~3600 lines)
styles.css   — Styling, responsive design, print styles
README.md    — User-facing documentation with evidence tables
```

## Architecture

### script.js Organization
1. **`scientificReferences`** (top) — PubMed-cited evidence for all calculations
2. **`figoClassification`** — FIGO/PALM-COEIN fibroid type definitions
3. **Risk calculators** — `calculateROMAScore()`, `calculateRMI()`, `assessIOTASimpleRules()`, `calculateADNEXScore()`
4. **Export/Print** — `exportResults()`, `printResults()`, `showNotification()`
5. **`growthCalculators`** — Core calculation engines per mass type:
   - `endometrioma` — Li model integration, recurrence risk, treatment effects
   - `fibroid` — Volume-based growth, FIGO, multiplicity, race/age adjustment
   - `simple-cyst` — Resolution modeling, ROMA/RMI, PCOS effects
   - `complex-cyst` — Subtype-specific (hemorrhagic/dermoid/serous/mucinous/etc), IOTA
   - `adenomyosis` — Type-specific (diffuse vs focal), JZ thickness, MUSA features
6. **`dynamicInputConfigs`** — HTML templates for type-specific form inputs
7. **UI Functions** — `selectGrowthType()`, `backToSelection()`, `getFormData()`, `calculateGrowth()`, `displayResults()`
8. **Recommendation generators** — `generateRecommendations()`, `generateClinicalSummary()`, `generateWarnings()`

### Data Flow
1. User selects mass type → `selectGrowthType()` injects dynamic form fields
2. Form submit → `getFormData()` collects all inputs into `data` object
3. `growthCalculators[type](data)` → returns `results` object
4. `generateMultiTimeProjections()` → multi-timepoint forecasts
5. `displayResults()` → populates all result DOM elements
6. References, recommendations, warnings generated from results

### Calculation Modes
- **Deterministic** (default) — Uses median/most-likely values, reproducible
- **Probabilistic** — Uses `Math.random()` with research-derived distributions

## Key Scientific References (Verified PMIDs)
| Topic | PMID | First Author |
|-------|------|-------------|
| Endometrioma natural history | 36902645 | Muzii L |
| Endometrioma natural history (2024) | 38337178 | Knez J |
| Endometriosis recurrence | 19279046 | Guo SW |
| OCP recurrence prevention | 18241819 | Vercellini P |
| Endometrioma treatment meta-analysis | 37944155 | Eberle A |
| Dienogest for endometrioma | 39324359 | Huang Y |
| Fibroid growth dynamics | 19047643 | Peddada SD |
| Myomectomy recurrence | 25331441 | Bhave Chittawar P |
| Fibroid race variation | 9397113 | Marshall LM |
| GnRH antagonist fibroid meta-analysis | 39821450 | Sanchez Martin MJ |
| Fibroid growth in pregnancy | 35981916 | Mitro SD |
| Ovarian cyst natural history | 20096820 | Greenlee RT |
| Postmenopausal cyst risk | 12962948 | Modesitt SC |
| Dermoid growth rate (1997) | 9314922 | Caspi B |
| Dermoid growth rate (2010) | 20201114 | Hoo WL |
| Dermoid malignant transformation | 39707031 | Jordan H |
| Hemorrhagic cyst diagnosis | 15840791 | Patel MD |
| O-RADS system | 31687921 | Andreotti RF |
| O-RADS v2022 validation | 39604652 | Almalki YE |
| O-RADS + CA-125 combined | 39344149 | Vo TQN |
| ADNEX Phase 6 validation | 40653066 | Moro F |
| ADNEX non-expert performance | 40283606 | Chankrachang A |
| Adenomyosis progression | 38738458 | Borghese G |
| MUSA consensus | 25652685 | Van den Bosch T |
| MUSA subtypes & fertility | 41081491 | Wang L |
| JZ thickness criteria | 8633139 | Reinhold C |
| ROMA algorithm | 18851871 | Moore RG |
| RMI index | 2223684 | Jacobs I |
| IOTA Simple Rules | 18504770 | Timmerman D |
| HE4 + CA-125 cutoffs | 39568971 | Kumari S |

## Development Notes

### Known Limitations
- **Li et al. predictive model**: The original paper (AUC 0.825) could not be verified via PubMed. The lab value integration (FSH, LH, cholesterol, LDL) is retained as approximate clinical estimates but the specific PMID is marked as unverified.
- **Confidence intervals**: Displayed ranges are estimated approximations (measurement error + growth variance), not formal statistical 95% CIs from individual studies. They are labeled as "Possible Size Range."
- **O-RADS categorization**: Uses an approximate risk-percentage mapping rather than the full morphology-based O-RADS criteria.

### Conventions
- All growth rates are stored as **cm/year** or **%/month** (volume)
- Volume calculations use sphere formula: V = (4/3)π(d/2)³
- All PMIDs must be verified against pubmed.ncbi.nlm.nih.gov before adding
- Deterministic mode must never use `Math.random()`
- Treatment effects should be applied after baseline growth is established
- Age adjustments for any given metric should only be applied once (avoid double-counting)

### Common Pitfalls
- Adenomyosis hides the `currentSize` field — fallback to estimated size from JZ thickness
- Dynamic inputs are injected as HTML strings — DOM element references must be queried after injection
- When adding new treatment options to dropdowns, the calculator switch/if logic must also handle them
- Each mass type has its own form field IDs (e.g., `endoTreatment` vs `fibroidTreatment` vs `adenomyosisTreatment`)

### Testing
Open `index.html` in a browser. Test each of the 5 mass types with:
1. Deterministic mode — same inputs should give same outputs every time
2. Probabilistic mode — outputs should vary within expected ranges
3. Edge cases: minimum age (15), maximum size (30cm), all risk factors checked
4. Adenomyosis without uterine volume (should use JZ-based estimate)
