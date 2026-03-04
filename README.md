Haselburg Marteloscope Stem Volume Analysis

Project Description

This project calculates stem volumes for trees in the Haselburg Marteloscope using species-specific allometric equations from Zianis et al. (2005).

Method Used:

-   Equations are from the Zianis et al. (2005)
-   Species-specific parameters from published literature
-   Validation against reference volumes

Aurthor

Student: Hassan Akhter

Student Number:24215861

Date: 10/02/2026

Course: Forest Information Technology - Applied Programming

Installation

Requirements

-   Python
-   Jupyter Notebook or Juypterlab

Install Dependencies

pip install -r requirements.txt

Project Structure

    Tree_volume_Project/
    ├── data/  # Input data file
    ├── plots/  # All output plots save here
    ├── final_result/  # Calculated Volume result save in csv file
    ├── code.ipynb # Main Jupyter Notebook
    ├── readme.txt # This file
    └── requirements.txt # Python dependences

Usage

Running the Analysis

1.  Open the jupter notebook:

-   code.ipynb

1.  Run all cells:

-   Click "Cell", "Run All"
-   Or run each cell individually with Shift+Enter

1.  Check outputs:

The analysis will create several files in the different folders of this directory:

-   haselberg_volume_results.csv - Complete results
-   parity_plot.png - Validation plot
-   distribution_plot.png - Data Distribution
-   boxplot_species.png - Volume by species
-   residual_plot.png - Error analysis

Input Data

File: 'M_scope_Haselburg_final.xlsx'

Required Columns:

-   Tree No: Tree identification Number
-   TrSpec: Tree species name
-   d 1.3 [cm]: Diameter at breast height (1.3m) in centimeters
-   h [m]: Tree height in meters
-   V [m³]: Reference volume for validation (optional)

Species with specific parameters:

-   Fagus sylvatica (European Beech)
-   Quercus robur (Pedunculate Oak)
-   Picea abies (Norway Spruce)
-   Betula pendula (Silver Birch)
-   Pinus sylvestris (Scots Pine)
-   Larix decidua
-   Acer pseudoplatanus
-   Carpinus betulus (It is not parameterized in Zianis et al. (2005), so volume calculations are not performed for this species.)

Method Description

Alometric Equation (Zianis et al., 2005)

Fagus sylvatica (Beech)

Country: Germany
V = a + b * DBH * H² + c × DBH³

Quercus robur, Picea Abies, Betula pendula, Larix decidua, Acer
pseudoplatanus

Country : Belgium

V = a + b × DBH + c × DBH² + d × DBH³ + e × H + f × DBH² × H

Pinus sylvestris

Country : Germany

V = a × DBH^(b) × H^(c)

where:

-   V = Stem Volume (meter cubic)
-   DBH = Diameter at breast height (cm)
-   H = Tree height (m)
-   a, b, c, d, e, f = Species-specific parameters from Zianis et al.
    (2005)

Species-Specific Parameters

Parameters are selected from Zianis et al. (2005) based on:

1.  Tree species identification
2.  Countries (Germany & Belgium)
3.  Available measurements (DBH and height)

Analysis Components

1. Data Loading

-   Reads tree measurements from Excel
-   Validates data completeness
-   Prepares dataset for analysis

2. Volume Calculation

-   Applies Zianis equations with species-specific parameters
-   Processes all trees in the dataset
-   Stores results in dataframe

3. Validation

Compare calculated volumes with reference volumes

Calculates error metrics:

-   R-squared (Coefficient of Determination)
-   RMSE (Root Mean Square Error)
-   Bias (Mean Error)
-   MAE (Mean Absolute Error)
-   MAPE (Mean Absolute Percentage Error)

4. Statistical Analysis

-   Summary statistics for all trees
-   Species-specific statistics
-   Distribution analysis

5. Visualizations

-   Parity Plot: Calculated vs reference volumes
-   Distribution Plots: DBH, height, and volume distributions
-   Box Plot: Volume distribution by species
-   Scatter Plot: DBH-volume relationship by species
-   Residual Plot: Error distribution analysis

Output Files

1. final_result/HaselBurg_Volume_Results.csv

Complete result table containing:

-   Tree number
-   Species
-   DBH and height measurements
-   Calculated volume
-   Reference volume

2. Visualization files (plots folder)

-   parity_plot.png - Validation against reference
-   distribution_plots.png - Four distribution plots
-   boxplot_species.png - Volume by species
-   residual_plot.png - Error analysis


Result Summary

Summary of Analysis

This analysis successfully calculated the stem volumes for the Haselburg Marteloscope using the allometric equations from Zianis et al. (2005), applying species-specific parameters and, where applicable, country-specific formulas. The analysis included 312 trees across 8 species, with a focus on ensuring accurate representation of species-specific growth patterns.

1.  Dataset Characteristics:
    -   Total trees analyzed : 312
    -   Number of species: 8
    -   Dominant species: Fagus Sylvatica (European Beech)

2.  Volume Results:
    -   Average calculated volume: 1.557 m³
    -   Volume range: 0.039 to 7.932 m³
    -   Total stand volume: 473.32 m³

3.  Validation Results:
    -   R² = 0.9317 means, 93.17% of variance explained
    -   RMSE = 0.3412 m³, typical error per tree is ±0.3412 m³
    -   Bias (Mean Error) = -0.0029 m³, negligible bias
    -   MAE = 0.1659 m³, average absolute error
    -   MAPE = 9.90%, average error relative to tree volume

Interpretation:

The Zianis equations provide very good agreement with reference volumes. Errors are small, bias is nearly zero, and variance is largely explained.

1.  Species-Specific Observations:
    -   Fagus sylvatica is dominant and contributes the largest proportion of total volume.
    -   Pinus sylvestris shows the highest average tree volume.
    -   Carpinus betulus is not parameterized in Zianis et al. (2005)
    -   Single-tree species (Larix decidua, Quercus robur) have limited influence on overall statistics but are included for completeness.

Method Assessment:

Strengths:

-   Simple to implement (only requires DBH and tree height).
-   Species-specific parameters capture difference in grwoth form.
-   Based on extensive empirical data ensures robustness.
-   Validation confirms strong agreement with reference data (R² > 0.93, low RMSE and negligible bias).

Limitations:

-   Minor discrepancies may arise from using country-specific equations for species outside Germany.
-   Extreme individual trees (very large or very small) contribute desproportionately to max/min ratios.

Recommendations:

1.  The Zianis allometric equations are suitable for stem volume estimation in the Haselberg Marteloscope.
2.  For species not in the original publication (e.g., Carpinus betulus), volume calculations are not performed. Use alternative estimation methods if these species are important.
3.  Consider local calibration where high precision is needed or for species with extreme sizes.
4.  Regular validation against measured volumes is recommended to maintain accuracy over time.

Conclusion:

The Zianis allometeric equations provide accurate stem volume estimates for the Haselburg Marteloscope with excellent agreement to reference volumes.

Troubleshooting

Common Issues

1. Excel file not found

FileNotFoundError: M_scope_Haselburg_final.xlsx

Solution: Make sure the Excel file is in the same directory as the notebook.

2. Missing libraries

ModuleNotFoundError: No module named 'pandas'

Solution: Intall requirements: 'pip install -r requirements.txt'

3. Permission errors when saving files

Solution: Make sure you have write permissions in the directory.

4. Plots not showing

Solution: Make sure matplotlib backend is configured. Add '%matplotlib inline' at the top of notebook

References

Primary Reference:

Zianis, D., Muukkonen, P., Mäkipää, R., & Mencuccini, M. (2005). Biomass and stem volume equations for tree species in Europe. Silva Fennica Monographs 4. 63 p.

Additional Reference:

-   Pandas Documentation: https://pandas.pydata.org/
-   Matplotlib Documentation: https://matplotlib.org/
-   Jupyter Documentation: https://jupyter.org/

License and Usage

This project was created for my university as part of forest information technology course.
