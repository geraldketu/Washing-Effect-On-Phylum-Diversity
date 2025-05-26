🧼 The Edge – SCI 101L Microbiome Diversity Project
📘 Project Title
How Showering Affects Belly Button Microbiome Phylum Diversity

👥 Group Name
The Edge

🧪 Purpose
This project investigates the relationship between personal hygiene habits—specifically shower frequency—and belly button microbiome phylum diversity. Our broader goal is to better understand how modern hygiene practices may unintentionally reduce microbial diversity on the skin, which plays a key role in immune health and skin homeostasis.

🧬 Hypothesis
We hypothesized that increased shower frequency would lead to reduced phylum diversity in the belly button microbiome.

📊 Dataset
Our dataset was sourced from a belly button microbiome survey and included:

Participant metadata (e.g., gender, age, shower frequency)

Phylum-level counts of microbial species per participant

Alpha-diversity metrics (Shannon and Simpson indices)

While we initially considered using Phinch for data visualization, we transitioned to Python notebooks due to limitations in format compatibility and data manipulation flexibility.

🧮 Methods
1. Data Cleaning
Removed missing or inconsistent entries

Extracted relevant variables: shower frequency (independent) and phylum counts/diversity (dependent)

2. Statistical Analysis
Pearson’s Correlation
Formula:

𝑟
=
C
o
v
(
𝑋
,
𝑌
)
𝜎
𝑋
⋅
𝜎
𝑌
r= 
σ 
X
​
 ⋅σ 
Y
​
 
Cov(X,Y)
​
 
where covariance measures how 
𝑋
X and 
𝑌
Y vary together, and 
𝜎
σ is standard deviation.

Results:

r = 0.0106: Indicates a negligible linear relationship between shower frequency and phylum diversity.

p = 0.8957: High p-value suggests the observed correlation is not statistically significant.

Linear Regression
Model:

𝑦
=
𝛽
0
+
𝛽
1
𝑥
y=β 
0
​
 +β 
1
​
 x
where 
𝑦
y = phylum count, 
𝑥
x = shower frequency.

Results:

Intercept (β₀) = 6.02: Baseline phylum count when shower frequency is zero.

Slope (β₁) = 0.01: Each additional shower per week is associated with an increase of 0.01 phyla, a negligible effect.

R² = 0.000: Shower frequency explains none of the variation in phylum diversity.

3. Justification for Method Selection
ANOVA: Requires categorical independent variables; our independent variable (shower frequency) is continuous.

Chi-Square: Suitable for categorical data; not ideal for continuous counts or correlation.

Grubbs' Test: Used to detect outliers; not appropriate for modeling relationships between variables.

📈 Visualization
Created bar graphs to show differences in phylum counts across shower frequencies.

Used regression plots to display trendlines and linear relationships.

🧪 Interpretation
The negligible correlation and regression results suggest that shower frequency does not significantly impact belly button microbiome phylum diversity.

This challenges the initial hypothesis and indicates that other factors may play a more substantial role in influencing microbial diversity.

📚 Key Concepts
Covariance
Measures how two variables change together.

Positive covariance indicates that variables increase together; negative covariance indicates that as one increases, the other decreases.

Shannon Diversity Index (H′)
Formula:

𝐻
′
=
−
∑
𝑖
=
1
𝑆
𝑝
𝑖
ln
⁡
(
𝑝
𝑖
)
H 
′
 =− 
i=1
∑
S
​
 p 
i
​
 ln(p 
i
​
 )
where 
𝑆
S is the total number of species and 
𝑝
𝑖
p 
i
​
  is the proportion of species 
𝑖
i.

Sensitive to both the richness (number of species) and evenness (distribution of species) in a community.

Simpson Diversity Index (D)
Formula:

𝐷
=
∑
𝑖
=
1
𝑆
𝑝
𝑖
2
D= 
i=1
∑
S
​
 p 
i
2
​
 
where 
𝑝
𝑖
p 
i
​
  is the proportion of species 
𝑖
i.

Emphasizes the dominance of species in a community; lower values indicate higher diversity.

⚠️ Limitations
Small sample size may limit the generalizability of results.

Self-reported shower frequency may introduce bias.

Focused only on phylum-level diversity; genus or species-level analyses may provide more detailed insights.

📂 Files Included
data_cleaning.ipynb: Data loading and preprocessing.

modeling.ipynb: Correlation and regression analysis.

presentation.pptx: Project presentation slides.

dataset_metadata.csv: Metadata associated with the dataset.

✅ Conclusion
Our analysis indicates that shower frequency has a negligible impact on belly button microbiome phylum diversity. This suggests that other factors, such as genetics, environment, or diet, may play more significant roles in shaping the skin microbiome.
