### 1. Load & Inspect Data

- Read OTU sheet and metadata sheet from Excel  
- Verify that OTU table contains `Phylum` plus per‑sample count columns  
- Verify that metadata contains `ID` and `Wash_Freq of BB (# times per week)`

```python
import pandas as pd

xls = pd.ExcelFile("Belly Button Batch2_OTU and Metadata_17Nov14.xlsx")
otu = pd.read_excel(xls, sheet_name=0)
meta = pd.read_excel(xls, sheet_name=1)
```

### 2. Prune Taxonomy Columns
-Drop all taxonomic ranks except    `Phylum`
-Keep only the columns needed for aggregation

```python
otu.drop(columns=[
    'Kingdom/Domain', 'Class', 'Order',
    'Family', 'Genus', 'Family_Genus'
], inplace=True)
```

### 3. Aggregate by Phylum
-Sum OTU counts so each row corresponds to one phylum

-Reset the index to turn `Phylum` back into a column

``` python
otu = otu.groupby('Phylum').sum().reset_index()
```

### 4. Compute Phylum Richness
-Transpose the table so each row is a sample (`ID`) and each column a phylum

-Count the number of phyla with nonzero counts for each sample

```python
otu_t = (
    otu.set_index('Phylum')
       .T
       .reset_index()
       .rename(columns={'index': 'ID'})
)

otu_t['NumPhylum'] = (otu_t.drop(columns='ID') > 0).sum(axis=1)
```
### 5 . Merge with Wash Frequency
-Select only the `ID` and wash frequency columns from metadata
-Inner‐join with the phylum richness table on `ID`

```python

meta_clean = meta[['ID', 'Wash_Freq of BB (# times per week)']]
df = otu_t.merge(meta_clean, on='ID', how='inner')

```

### 6. Handle Missing Values
-Replace `Unknown` wash frequencies with `NaN`

-Drop samples lacking a numeric wash frequency

-Reset index and save the cleaned table

```python
import numpy as np

df['WashFreq'] = (
    df['Wash_Freq of BB (# times per week)']
      .replace('Unknown', np.nan)
      .astype(float)
)
df.dropna(subset=['WashFreq'], inplace=True)
df.reset_index(drop=True, inplace=True)
df.to_csv('data/clean_phylum_washFreq_BB.csv', index=False)
```
### 7. Statistical Analysis

#### Linear Regression

Fit a simple linear model:

$$
\text{NumPhylum} = \beta_0 + \beta_1 \times \text{WashFreq}
$$

- **β₀ (intercept):** baseline phylum count  
- **β₁ (slope):** change in phylum count per additional wash/week  
- **R²:** fraction of variance explained  

Implement with `sklearn.linear_model.LinearRegression`:

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
# X = df[['WashFreq']], y = df['NumPhylum']
model.fit(X, y)

