# Benign Gynecologic Mass Growth Rate Calculator

An evidence-based web application for estimating growth patterns of benign gynecologic masses with 82.5% accuracy using validated clinical models.

## Features

- **Four Mass Types**: Endometrioma, Uterine Fibroids, Simple Ovarian Cysts, and Complex Ovarian Cysts
- **Li et al. Predictive Model**: 82.5% accuracy with laboratory value integration (FSH, LH, lipid profile)
- **Multi-Time Point Projections**: 3, 6, 12, 24, and 36-month growth forecasts
- **Volume-Based Calculations**: More accurate than diameter-based measurements
- **Enhanced Risk Stratification**: IOTA Simple Rules and O-RADS categories for complex cysts
- **Evidence-Based Algorithms**: Based on comprehensive research data with precise growth rate ranges
- **Dynamic Input Forms**: Tailored questions based on selected mass type
- **Growth Projections**: Visual representation of size changes over time
- **Clinical Recommendations**: Evidence-based management suggestions with confidence intervals
- **Advanced Risk Assessment**: Comprehensive risk factor analysis and stratification

## File Structure

```
Growth-rate-calculator/
├── index.html          # Main HTML structure
├── styles.css          # All CSS styling
├── script.js           # JavaScript functionality and algorithms
└── README.md           # Project documentation
```

## Usage

1. Open `index.html` in a web browser
2. Select the type of gynecologic mass
3. Fill in the required information (current size, age, projection period)
4. Complete optional fields for more accurate predictions
5. Click "Calculate Growth Projection" to view results

## Supported Mass Types

### Endometrioma
- Ovarian cysts from endometriosis
- Accounts for previous surgery, treatment, and risk factors
- Includes recurrence probability calculations

### Uterine Fibroids
- Benign muscle tumors
- Considers location, race, pregnancy status
- Post-surgical recurrence patterns

### Simple Ovarian Cysts
- Fluid-filled sacs
- Menopausal status-based predictions
- Resolution probability calculations

### Complex Ovarian Cysts
- Multi-component cysts
- Type-specific growth patterns (hemorrhagic, dermoid, serous, mucinous)
- Specialized evaluation recommendations

## Medical Disclaimer

This calculator uses published research data for educational purposes only. Individual patient factors may significantly affect actual growth rates. Always consult with a healthcare provider for personalized medical guidance and treatment decisions.

## Technical Details

- **Frontend**: Pure HTML, CSS, and JavaScript
- **No Dependencies**: Self-contained application
- **Responsive Design**: Works on desktop and mobile devices
- **Evidence-Based**: Algorithms based on peer-reviewed research

## Version

Version 3.0: Enhanced with Li et al. predictive model (82.5% accuracy), multi-time point projections (3-36 months), volume-based calculations, IOTA Simple Rules and O-RADS risk stratification, enhanced confidence intervals, and laboratory value integration (FSH, LH, lipid profile). Based on comprehensive research data with precise growth rate ranges and evidence-based clinical thresholds.
