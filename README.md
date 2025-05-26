
## Purpose  
This project investigates the relationship between personal hygiene habits—specifically shower frequency—and belly button microbiome phylum diversity. Our broader goal is to better understand how modern hygiene practices may unintentionally reduce microbial diversity on the skin, which plays a key role in immune health and skin homeostasis.

## Hypothesis  
We hypothesized that increased shower frequency would lead to reduced phylum diversity in the belly button microbiome.

## Dataset  
Our dataset was sourced from a belly button microbiome survey and included:  
- Participant metadata (e.g., gender, age, shower frequency)  
- Phylum-level counts of microbial species per participant  
- Alpha-diversity metrics (Shannon and Simpson indices)  

While we initially considered using [Phinch](https://phinch.org/) for data visualization, we transitioned to Python notebooks due to limitations in format compatibility and data manipulation flexibility.

## Methods

### 1. Data Cleaning  
- Removed missing or inconsistent entries  
- Extracted relevant variables: shower frequency (independent) and phylum counts/diversity (dependent)

### 2. Statistical Analysis  

#### Pearson’s Correlation  
**Formula**:  
Let $X$ = shower frequency and $Y$ = phylum count.

**Covariance**:  
$$
\text{Cov}(X, Y) = \frac{1}{n - 1} \sum_{i=1}^n (X_i - \bar{X})(Y_i - \bar{Y})
$$

**Pearson’s correlation coefficient**:  
$$
r = \frac{\text{Cov}(X, Y)}{\sigma_X \sigma_Y}
$$

**Results**:  
- $r = 0.0106$: Indicates a negligible linear relationship  
- $p = 0.8957$: High p-value suggests the observed correlation is not statistically significant  

#### Linear Regression  
**Model**:  
$$
y = \beta_0 + \beta_1 x
$$

Where:
- $y$ = predicted phylum count  
- $x$ = shower frequency  
- $\beta_0$ = intercept  
- $\beta_1$ = slope

**Results**:  
- Intercept ($\beta_0$) = 6.02: Baseline phylum count when shower frequency is zero  
- Slope ($\beta_1$) = 0.01: Each additional shower per week is associated with an increase of 0.01 phyla  
- $R^2 = 0.000$: Shower frequency explains none of the variation in phylum diversity  

### 3. Justification for Method Selection  
- **ANOVA**: Requires categorical independent variables  
- **Chi-Square**: Suitable for categorical data, not continuous variables  
- **Grubbs' Test**: Used to detect outliers, not relationships between variables  

## Visualization  
- Bar graphs of phylum counts across shower frequency  
- Scatterplot with regression line for visualizing trends  

## Interpretation  
The negligible correlation and regression results suggest that shower frequency does not significantly impact belly button microbiome phylum diversity. This challenges our hypothesis and indicates that other factors may play a more substantial role.

## Key Concepts  

### Covariance  
Measures how two variables vary together:

$$
\text{Cov}(X, Y) = \frac{1}{n - 1} \sum (X_i - \bar{X})(Y_i - \bar{Y})
$$

- Positive covariance: variables increase together  
- Negative covariance: one increases while the other decreases  

### Shannon Diversity Index  
A measure of both species richness and evenness.

**Formula**:  
$$
H' = -\sum_{i=1}^S p_i \ln(p_i)
$$

Where:
- $p_i$ is the proportion of species $i$  
- $S$ is the total number of species  

### Simpson Diversity Index  
Emphasizes dominant species by squaring proportions.

**Formula**:  
$$
D = \sum_{i=1}^S p_i^2
$$

Lower values indicate higher diversity.

## Limitations  
- Small sample size  
- Self-reported shower frequency may introduce bias  
- Focused only on phylum-level diversity  

## Files Included  
- `data_cleaning.ipynb`: Data loading and preprocessing  
- `modeling.ipynb`: Correlation and regression analysis  
- `presentation.pptx`: Project slides  
- `dataset_metadata.csv`: Participant metadata  

