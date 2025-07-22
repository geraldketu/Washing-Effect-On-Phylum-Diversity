<!-- README.md -->

# How does showering affect your bellybutton Microbiome ?

## Purpose  
In this project, I explored whether the frequency of belly‑button washing influences phylum‑level microbial richness. The goal was to understand if more frequent washing disrupts or reduces the number of distinct phyla present.

## Hypothesis  
I hypothesized that increased wash frequency would correlate with decreased phylum richness, as over‑cleansing might remove loosely attached taxa.

## Dataset  
- **Source** [Rob Dunn Lab, NC State, bellybutton dataset](https://robdunnlab.com/projects/belly-button-biodiversity/)
- **OTU counts** aggregated at the phylum rank (raw counts per sample)  
- **Metadata** containing sample `ID` and `Wash_Freq of BB (# times per week)`  

After cleaning and merging, the final table (`clean_phylum_washFreq_BB.csv`) includes:  
- `ID`  
- `NumPhylum` (count of phyla detected)  
- `WashFreq` (washes per week)

## Methods  
Detailed steps for data cleaning and statistical analysis are provided in **methods.md**.

## Results & Interpretation  
Full results and their biological interpretation appear in **analysis.md**.

---

```bash
# Quick start
git clone https://github.com/geraldketu/Washing-Effect-On-Phylum-Diversity.git
cd Washing-Effect-On-Phylum-Diversity
pip install pandas numpy scikit-learn matplotlib
jupyter lab
```

