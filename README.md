# Showering and Belly Button Microbiome Diversity

## Purpose  
In this project, I explored whether the frequency of showering affects phylum-level diversity in the belly button microbiome. The idea was to better understand how modern hygiene habits may influence our skin’s microbial ecosystem.

## Hypothesis  
I hypothesized that the more a person showers, the fewer microbial phyla would be present in their belly button due to over-cleansing or disruption of natural flora.

## Dataset  
I used a cleaned version of the Belly Button Biodiversity dataset, which included:
- Participant metadata (age, gender, shower frequency)
- Microbial species count by phylum
- Diversity indices such as Shannon and Simpson


## Methods

### Data Cleaning  
I cleaned the dataset by removing null or irrelevant fields, filtered to keep only participants with complete shower frequency data, and aggregated OTU (Operational Taxonomic Unit) data by phylum.

### Statistical Analysis  

#### Pearson’s Correlation  
To check for linear association between shower frequency and phylum diversity, I used Pearson's correlation.  

**Covariance Formula** (used in Pearson's r):  
`Cov(X, Y) = (1 / (n - 1)) * Σ(Xi - X̄)(Yi - Ȳ)`

Where:  
- `X` is shower frequency  
- `Y` is phylum count  
- `X̄` and `Ȳ` are their respective means  

Pearson’s `r` was calculated using the formula:  
`r = Cov(X, Y) / (σ_X * σ_Y)`

**Results**:
- `r = 0.0106`: Very weak linear correlation  
- `p = 0.8957`: Not statistically significant  

#### Linear Regression  
I also used a simple linear regression model to see if shower frequency could predict the number of phyla.

**Model**:  
`y = β₀ + β₁x`  
Where:  
- `y` = predicted phylum count  
- `x` = shower frequency  
- `β₀` = intercept  
- `β₁` = slope  

**Results**:  
- `β₀ = 6.02`: Baseline diversity when shower frequency is 0  
- `β₁ = 0.01`: Each additional shower per week increases phylum count by 0.01  
- `R² = 0.000`: Shower frequency explains virtually none of the variation in diversity  

## Key Concept: Covariance  
Covariance measures how two variables change together.  

Formula:  
`Cov(X, Y) = (1 / (n - 1)) * Σ(Xi - X̄)(Yi - Ȳ)`

- A positive value means both variables increase together  
- A negative value means when one increases, the other decreases  
- A value near zero means no clear trend  

## Conclusion  
The analysis shows no statistically significant relationship between how often someone showers and how diverse their belly button microbiome is. While I expected more frequent showering to reduce diversity, the data suggests otherwise—or at least that any effect is too small to detect with this dataset.

 
