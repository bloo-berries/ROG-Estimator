# Benign Gynecologic Mass Growth Rate Calculator

An evidence-based web application for estimating growth patterns of benign gynecologic masses with enhanced accuracy using validated clinical models and latest research data.

## Version 8.0 Features

### New in Version 8.0

- **Deterministic Calculation Mode**: Choose between deterministic (reproducible median values) and probabilistic (statistical distribution) calculation modes
- **ROMA Score Calculator**: Risk of Ovarian Malignancy Algorithm using CA-125 and HE4 tumor markers
- **RMI Calculator**: Risk of Malignancy Index integration for comprehensive malignancy risk assessment
- **FIGO/PALM-COEIN Classification**: Standardized fibroid classification system
- **IOTA Simple Rules**: Validated ultrasound-based malignancy risk assessment
- **Enhanced Confidence Intervals**: Prominently displayed 95% confidence intervals for all projections
- **Tumor Marker Integration**: CA-125 and HE4 input fields for malignancy risk calculation
- **Export/Print Functionality**: Export results as HTML report or print directly
- **Comprehensive Citation References**: PubMed IDs and citations for all evidence-based values

### Core Features

- **Five Mass Types**: Endometrioma, Uterine Fibroids, Simple Ovarian Cysts, Complex Ovarian Cysts, and Adenomyosis
- **Li et al. Predictive Model**: 82.5% accuracy with laboratory value integration (FSH, LH, lipid profile)
- **Multi-Time Point Projections**: 3, 6, 12, 24, and 36-month growth forecasts
- **Volume-Based Calculations**: More accurate than diameter-based measurements
- **Enhanced Risk Stratification**: IOTA Simple Rules and O-RADS categories for complex cysts
- **Evidence-Based Algorithms**: Based on comprehensive peer-reviewed research data

## Scientific Evidence Base

### Endometrioma Growth Rates
| Source | PMID | Key Finding |
|--------|------|-------------|
| Muzii L, et al. J Clin Med. 2023 | 36902645 | Median -1.7mm/year; 47% decrease, 31% stable, 22% increase |
| Guo SW. Hum Reprod Update. 2009 | 19279046 | OR 3.245 for previous history; 51% at 36 months untreated |
| Vercellini P, et al. Am J Obstet Gynecol. 2008 | 18241819 | 94% recurrence-free at 36 months with continuous OCP |

### Uterine Fibroid Growth Rates
| Source | PMID | Key Finding |
|--------|------|-------------|
| Peddada SD, et al. Proc Natl Acad Sci. 2008 | 19047643 | 9-89% growth over 18 months; 188% for <1cm fibroids |
| Bhave Chittawar P, et al. Cochrane. 2014 | 25331441 | 41.6% recurrence at 3 years (laparoscopic), 31-43% (open) |
| Marshall LM, et al. Obstet Gynecol. 1997 | 9397113 | 2-3x higher incidence in African American women |

### Ovarian Cyst Natural History
| Source | PMID | Key Finding |
|--------|------|-------------|
| Greenlee RT, et al. Am J Obstet Gynecol. 2010 | 20096820 | 70-80% resolve in 2-3 cycles (premenopausal) |
| Modesitt SC, et al. Obstet Gynecol. 2003 | 12962948 | 32% resolve at 1 year; 15-20% malignant potential (postmenopausal) |
| Caspi B, et al. Fertil Steril. 1997 | 9314922 | Dermoid: 1.8 mm/year; >2cm/year excludes dermoid |
| Patel MD, et al. J Ultrasound Med. 2005 | 15840791 | Hemorrhagic cyst sonographic diagnosis |

### Malignancy Risk Assessment
| Calculator | PMID | Performance |
|------------|------|-------------|
| ROMA | 18851871 | Sensitivity 92.3%, Specificity 76.0% |
| RMI | 2223684 | Sensitivity 70-87%, Specificity 89-97% |
| IOTA Simple Rules | 18504770 | Sensitivity 95%, Specificity 91% |
| O-RADS | 31687921 | Standardized risk categorization |

### Adenomyosis Progression
| Source | PMID | Key Finding |
|--------|------|-------------|
| Borghese G, et al. Int J Gynaecol Obstet. 2024 | 38738458 | 21.3% progression at 12 months; Focal outer myometrium = highest risk |
| Reinhold C, et al. Radiology. 1996 | 8633139 | Diagnostic threshold ≥12mm; Primary marker for diffuse type |
| Van den Bosch T, et al. Ultrasound Obstet Gynecol. 2015 | 25652685 | MUSA consensus — sonographic features of adenomyosis |

## Calculation Modes

### Deterministic Mode (Default)
- Uses median values from research for reproducible results
- Ideal for clinical documentation and comparison
- Same inputs will always produce the same outputs

### Probabilistic Mode
- Uses statistical distributions from research
- Models natural biological variability
- Results may vary between calculations

## Risk Assessment Tools

### ROMA Score (Risk of Ovarian Malignancy Algorithm)
Formula based on menopausal status:
- **Premenopausal**: PI = -12.0 + 2.38×ln(HE4) + 0.0626×ln(CA125)
- **Postmenopausal**: PI = -8.09 + 1.04×ln(HE4) + 0.732×ln(CA125)
- **ROMA** = exp(PI) / (1 + exp(PI)) × 100%
- **Cutoffs**: 7.4% (premenopausal), 25.3% (postmenopausal)

### RMI (Risk of Malignancy Index)
- **Formula**: RMI = U × M × CA-125
- **U (Ultrasound score)**: 0 = no features, 1 = one feature, 3 = 2+ features
- **M (Menopausal status)**: 1 = premenopausal, 3 = postmenopausal
- **Cutoff**: RMI ≥200 indicates high risk

### IOTA Simple Rules
Five B-features (Benign) and five M-features (Malignant):
- If only B-features present: Classify as benign
- If only M-features present: Classify as malignant
- If both or neither: Inconclusive - apply subjective assessment

### FIGO Classification (Fibroids)
- **Type 0-2**: Submucosal (high symptom risk)
- **Type 3-4**: Intramural (moderate symptom risk)
- **Type 5-7**: Subserosal (low symptom risk)
- **Type 8**: Other locations

## File Structure

```
ROG-Estimator/
├── index.html          # Main HTML structure with enhanced UI
├── styles.css          # CSS styling with new components
├── script.js           # JavaScript algorithms and calculators
└── README.md           # Documentation with evidence citations
```

## Usage

1. Open `index.html` in a web browser
2. Select the type of gynecologic mass
3. Choose calculation mode (deterministic or probabilistic)
4. Fill in required information (current size, age, projection period)
5. Complete optional fields for enhanced accuracy:
   - Tumor markers (CA-125, HE4) for malignancy risk
   - Ultrasound features for IOTA assessment
   - FIGO classification for fibroids
6. Click "Calculate Growth Projection" to view results
7. Export or print results as needed

## Supported Mass Types

### Endometrioma
- Growth distribution: 47% decrease, 31% stable, 22% increase
- Treatment effects: Continuous OCP reduces recurrence by 90%
- Li et al. model integration with laboratory values
- Recurrence risk stratification

### Uterine Fibroids
- Size-dependent growth (188% for <1cm, 9-89% for 2-5cm)
- FIGO/PALM-COEIN classification system
- Post-myomectomy recurrence prediction
- Race and age-adjusted algorithms

### Simple Ovarian Cysts
- Resolution rates: 70-80% in 2-3 cycles
- Postmenopausal risk assessment
- ROMA and RMI score integration
- PCOS-specific considerations

### Complex Ovarian Cysts
- Type-specific growth patterns
- IOTA Simple Rules assessment
- O-RADS risk stratification
- Full tumor marker integration

### Adenomyosis
- Evidence-based progression rates
- JZ thickness monitoring
- Type-specific algorithms (diffuse vs focal)
- Treatment response prediction

## Medical Disclaimer

This calculator uses published research data for educational purposes only. Individual patient factors may significantly affect actual growth rates. The risk calculators (ROMA, RMI, IOTA) are decision support tools and do not replace clinical judgment or histopathological diagnosis. Always consult with a healthcare provider for personalized medical guidance and treatment decisions.

## Technical Details

- **Frontend**: Pure HTML, CSS, and JavaScript
- **No Dependencies**: Self-contained application
- **Responsive Design**: Works on desktop and mobile devices
- **Print Optimized**: CSS print styles for clean output
- **Evidence-Based**: All algorithms cite peer-reviewed research

## Changelog

### Version 8.0 (Current)
- Added deterministic/probabilistic calculation modes
- Implemented ROMA Score Calculator
- Implemented RMI Calculator
- Added FIGO/PALM-COEIN classification
- Added IOTA Simple Rules assessment
- Enhanced confidence interval display
- Added tumor marker input fields
- Added export/print functionality
- Comprehensive PubMed citation system

### Version 7.0
- Added adenomyosis calculator
- Enhanced fibroid multiplicity assessment
- Improved treatment effectiveness data

### Previous Versions
- Initial implementation with basic growth calculations
- Added Li et al. predictive model
- Multi-time projections
- O-RADS integration
