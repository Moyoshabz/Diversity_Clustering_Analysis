# Diversity_Clustering_Analysis
### Uncovering Workforce Diversity Clusters Across Tech Companies: An Unsupervised Learning Approach

As someone passionate about equity and inclusion, I wanted to explore how diversity, especially gender and ethnicity is represented across major tech companies over time. Using real-world demographic data, I applied various data analysis, visualization, and clustering techniques to uncover patterns and insights.

This project was also an opportunity to deepen my skills in data cleaning, feature engineering, and unsupervised machine learning techniques like KMeans, Hierarchical Clustering, and the Shannon Diversity Index.

---

## Dataset
Source: Kaggle
Link

The dataset contains workforce demographic data from several tech companies spanning multiple years (2014–2019), including percentage breakdowns by ethnicity and gender.

---

## Data Cleaning & Preprocessing

- Removed rows with nulls and cleaned percentage fields by removing % signs and replacing hyphens (-) with NaN.

- Imputed missing values in demographic columns with 0 for meaningful calculation.

```
percent_cols = ['% Asian', '% Latino', '% Black', '% Multi', '% Other', '% Undeclared']
# Cleaned and converted to numeric
for col in percent_cols:
    df[col] = df[col].replace('-', np.nan)
    df[col] = df[col].astype(str).str.replace('%', '', regex=False).str.strip()
    df[col] = pd.to_numeric(df[col], errors='coerce')
df[percent_cols] = df[percent_cols].fillna(0)

```

---

## Exploratory Data Analysis (EDA)

- Correlation Heatmap: Helped understand relationships between gender, ethnicity, and other demographic fields.

- Gender Trends: Line plot showed how the average percentage of females evolved over time.

---

## Feature Engineering

- Created a Gender Imbalance feature to quantify disparity between male and female representation.

- Normalized ethnicity percentages by row totals to ensure consistent comparison.

- Calculated Shannon Diversity Index to measure workforce diversity across companies.

---

## Diversity Insight (Shannon Index)

Using the Shannon Index, I calculated workforce diversity based on ethnicity data. Notable findings for 2018:

- Most Diverse:
    - Netflix (1.996)
    - Apple (1.964)
    - Amazon (1.962)

- Least Diverse:
    - Etsy (1.124)
    - HP (1.287)

Insight: Streaming and cloud-native companies are leading diversity efforts, while traditional enterprise/hardware firms lag behind.

---

## Visualization

Dominant Ethnicity Plot: Bar chart showing which ethnic group was most dominant per company in 2018.
-- add image here

---
## Clustering Analysis

K-Means Clustering (k = 5)

- Used the Elbow Method to determine optimal k.

- Clustered companies based on gender and ethnicity makeup.

- PCA was used to reduce dimensions for a 2D visualization of clusters.

--- 

## Hierarchical Clustering

- Used Ward’s method and plotted a dendrogram.
- Helped visualize how companies group together based on demographic similarity.

---
## Tools & Skills Learned

- Python Libraries: pandas, matplotlib, seaborn, scikit-learn, scipy

- Statistical Measures: Correlation, Shannon Index

- Clustering Techniques: KMeans, Hierarchical (Agglomerative)

- Dimensionality Reduction: PCA

- Data Cleaning: Handling % symbols, missing data, normalization
