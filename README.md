# Haselburg Marteloscope Stem Volume Analysis

**Author:** Hassan Akhter
**Student Number:** ******
**Date:** 10/02/2026
**Course:** Forest Information Technology - Applied Programming

## What is this project?

This project calculates stem volumes for trees in the Haselburg Marteloscope using species-specific allometric equations from Zianis et al. (2005). I applied country-specific parameters for
8 tree species and validated the results against reference volumes.


## Installation

**Requirements**
- Python
- Jupyter Notebook or JupyterLab

**Install dependencies**
```
pip install -r requirements.txt
```


## Project Structure
```
Tree_volume_Project/
├── data/           # Input data file
├── plots/          # All output plots saved here
├── final_result/   # Calculated volume results in CSV
├── code.ipynb      # Main Jupyter Notebook
├── README.md       # This file
└── requirements.txt
```



## How to Run

1. Open the notebook: `code.ipynb`
2. Run all cells:
   - Click **Cell** → **Run All**
   - Or run each cell with `Shift + Enter`
3. Check outputs in the `plots/` and `final_result/` folders

---

## Input Data

**File:** `M_scope_Haselburg_final.xlsx`

| Column | Description |
|---|---|
| Tree No | Tree identification number |
| TrSpec | Tree species name |
| d 1.3 [cm] | Diameter at breast height (1.3m) in cm |
| h [m] | Tree height in meters |
| V [m³] | Reference volume for validation (optional) |

**Species covered:**
- *Fagus sylvatica* (European Beech)
- *Quercus robur* (Pedunculate Oak)
- *Picea abies* (Norway Spruce)
- *Betula pendula* (Silver Birch)
- *Pinus sylvestris* (Scots Pine)
- *Larix decidua*
- *Acer pseudoplatanus*
- *Carpinus betulus* — not parameterized in Zianis et al. (2005), so volume is not calculated for this species

---

## Method

Allometric equations from Zianis et al. (2005):

**Fagus sylvatica** (Germany)
```
V = a + b × DBH × H² + c × DBH³
```

**Quercus robur, Picea abies, Betula pendula,
Larix decidua, Acer pseudoplatanus** (Belgium)
```
V = a + b × DBH + c × DBH² + d × DBH³ + e × H + f × DBH² × H
```

**Pinus sylvestris** (Germany)
```
V = a × DBH^(b) × H^(c)
```

Where:
- **V** = Stem volume (m³)
- **DBH** = Diameter at breast height (cm)
- **H** = Tree height (m)
- **a, b, c, d, e, f** = Species-specific parameters

---

## Results

| Metric | Value |
|---|---|
| Total trees analyzed | 312 |
| Number of species | 8 |
| Dominant species | Fagus sylvatica (European Beech) |
| Average calculated volume | 1.557 m³ |
| Volume range | 0.039 – 7.932 m³ |
| Total stand volume | 473.32 m³ |

**Validation against reference volumes:**

| Metric | Value | Meaning |
|---|---|---|
| R² | 0.9317 | 93.17% of variance explained |
| RMSE | 0.3412 m³ | Typical error per tree |
| Bias | -0.0029 m³ | Nearly zero — no systematic error |
| MAE | 0.1659 m³ | Average absolute error |
| MAPE | 9.90% | Average % error per tree |

The Zianis equations showed strong agreement with reference volumes — low error, negligible bias, and high R².

---

## Output Files

| File | Description |
|---|---|
| `final_result/HaselBurg_Volume_Results.csv` | Full results table |
| `plots/parity_plot.png` | Calculated vs reference volumes |
| `plots/distribution_plots.png` | DBH, height, volume distributions |
| `plots/boxplot_species.png` | Volume by species |
| `plots/residual_plot.png` | Error analysis |

---

## Troubleshooting

**Excel file not found**
```
FileNotFoundError: M_scope_Haselburg_final.xlsx
```
Make sure the Excel file is in the same folder as the notebook.

**Missing libraries**
```
ModuleNotFoundError: No module named 'pandas'
```
Run: `pip install -r requirements.txt`

**Plots not showing**
Add this at the top of the notebook:
```python
%matplotlib inline
```

---

## References

Zianis, D., Muukkonen, P., Mäkipää, R., & Mencuccini, M. (2005). *Biomass and stem volume equations for tree species in Europe.* Silva Fennica Monographs 4. 63 p.

- [Pandas Documentation](https://pandas.pydata.org/)
- [Matplotlib Documentation](https://matplotlib.org/)
- [Jupyter Documentation](https://jupyter.org/)

---

## License

This project was created for university as part of the Forest Information Technology - Applied Programming course.
