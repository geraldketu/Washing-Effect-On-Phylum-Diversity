
```markdown
<!-- analysis.md -->

# Results & Analysis

From `modeling.ipynb`, linear regression of **NumPhylum** on **WashFreq**:

| Metric                            | Value   |
|-----------------------------------|--------:|
| R² (coefficient of determination) | 0.000   |
| Intercept (β₀)                    | 6.02    |
| Slope (β₁)                        | 0.01    |

![Wash vs Phyla Scatter + Fit](./images/wash_vs_phylum.png)

## Interpretation  
- **R² ≈ 0**: Wash frequency explains virtually none of the variation in phylum richness.  
- **Intercept ≈ 6.02**: Even without washing, ~6 phyla are detected on average.  
- **Slope ≈ 0.01**: Each additional wash/week adds only ~0.01 phylum—statistically negligible.

### What This Tells Us  
Phylum‐level richness remains stable (~6 phyla/sample) regardless of washing frequency. This suggests that routine washing does not significantly alter which major phyla colonize the belly button. Other factors—such as host biology or environmental exposure—likely drive large‑scale phylum diversity.

---

_For full details and code, see `notebooks/modeling.ipynb`._
