


# Data Cleaning & Statistical Methods

## 1. Load & Inspect Data  
- Read OTU sheet and metadata sheet from Excel.  
- Verify columns: retain `Phylum` + sample counts; retain `ID` + wash frequency.

## 2. Prune Taxonomy Columns  
```python
otu.drop(columns=['Kingdom/Domain','Class','Order',
                  'Family','Genus','Family_Genus'],
         inplace=True)
3. Aggregate by Phylum
python
Copy
Edit
otu = otu.groupby('Phylum').sum().reset_index()
4. Compute Phylum Richness
python
Copy
Edit
otu_t = (otu.set_index('Phylum')
            .T
            .reset_index()
            .rename(columns={'index':'ID'}))
otu_t['NumPhylum'] = (otu_t.drop(columns='ID') > 0).sum(axis=1)
5. Merge with Wash Frequency
python
Copy
Edit
meta_clean = meta[['ID','Wash_Freq of BB (# times per week)']]
df = otu_t.merge(meta_clean, on='ID', how='inner')
6. Handle Missing Values
python
Copy
Edit
df['WashFreq'] = (df['Wash_Freq of BB (# times per week)']
                    .replace('Unknown', np.nan)
                    .astype(float))
df.dropna(subset=['WashFreq'], inplace=True)
df.reset_index(drop=True, inplace=True)
df.to_csv('data/clean_phylum_washFreq_BB.csv', index=False)
7. Statistical Analysis
Linear Regression
Fit a simple linear model:

NumPhylum
=
𝛽
0
+
𝛽
1
×
WashFreq
NumPhylum=β 
0
​
 +β 
1
​
 ×WashFreq
β₀ (intercept): baseline phylum count

β₁ (slope): change in phylum count per additional wash/week

R²: fraction of variance explained

Implement with sklearn.linear_model.LinearRegression.
