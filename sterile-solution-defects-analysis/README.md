# Statistical Analysis of Production Defects: Sterile Medical Solution

An academic statistics project (IBM SPSS) that studies how three sources of production defects relate to the total goods delivered to the warehouse for a sterile medical solution line, using 30 monthly observations (January 2017 to June 2019).

> The report contains aggregated monthly counts only. No company name, batch, product or personal data is included.

## Summary

Defects in sterile drug manufacturing are costly: every unit is expensive, defects disrupt the production plan, and serious defects can lead to recalls. The project compares three defect sources with total goods delivered:

| Code | Stage | What it covers |
|---|---|---|
| X1 | Manufacturing (BFS) | Blow-fill-seal: forming the plastic bottle, filling it and sealing it |
| X2 | Autoclave | Handling during loading, sterilization and unloading |
| X3 | Packaging | Labeling, film wrapping and cartoning |

Y is the total goods delivered to the warehouse.

## Method

1. Descriptive statistics and histograms for the four variables.
2. Spearman correlation matrix (the variables are right-skewed).
3. Simple linear regression of Y on each defect source.
4. Multiple linear regression with all three sources, then with the significant ones only.

## Key results (N = 30)

**Correlation with goods delivered (Spearman)**

| Defect source | Coefficient | Significant at 0.01 |
|---|---|---|
| BFS (X1) | 0.939 | Yes |
| Packaging (X3) | 0.924 | Yes |
| Autoclave (X2) | 0.895 | Yes |

**Regression models**

| Model | R² | Adjusted R² |
|---|---|---|
| Y ~ BFS | 0.971 | 0.970 |
| Y ~ Autoclave | 0.961 | 0.960 |
| Y ~ Packaging | 0.966 | 0.964 |
| Y ~ BFS + Autoclave + Packaging | 0.984 | 0.982 |
| Y ~ BFS + Packaging | 0.981 | 0.980 |

In the full model the autoclave coefficient is borderline (p = 0.053) while BFS (p = 0.002) and packaging (p = 0.029) are significant. Autoclave and BFS defects are very strongly correlated (0.951), so autoclave adds little once BFS is in the model. The model with BFS and packaging was selected:

`Y = 55.095 x BFS + 441.221 x Packaging` (constant not significant, p = 0.948)

## Recommendations in the report

- Run a root-cause analysis of the BFS stage (for example, machine spare parts).
- Identify which packaging machines produce the highest defect rate.

## Limitations and next steps

- **The high correlations partly reflect production scale.** All four series grow with production volume (the histograms show a few very high-volume months), so defect counts rise when output rises. The regressions describe association, not an effect of defects on output.
- **A rate-based view would compare stages more fairly.** Defect rate (defects per unit produced), a Pareto chart and control charts by stage are the natural follow-up. From the reported means, autoclave accounts for about 60% of defect counts, BFS about 37% and packaging about 3%, so autoclave should still be monitored even though it is not significant in the regression.
- **Small sample and collinearity.** 30 monthly points with strongly correlated predictors make individual coefficients unstable.

## Repository structure

```
sterile-solution-defects-analysis/
├── README.md
└── report/    Project_of_Stat_by_Aboelanen.pdf
```

## Tools

IBM SPSS Statistics (descriptive statistics, Spearman correlation, linear regression).

## Author

Ahmed Aboelanen, supply chain analyst.
