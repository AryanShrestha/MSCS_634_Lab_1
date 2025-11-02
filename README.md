# MSCS_634_Lab_1 – Data Visualization and Statistical Analysis

**Author:** Aryan Shrestha  
**Course:** MSCS 634 – Data Mining  

## Dataset
Used Kaggle dataset **sample-superstorecsv** by *konstantinognev* and placed the file
`SampleSuperstore.csv` into the `data/` folder.

Kaggle page: https://www.kaggle.com/datasets/konstantinognev/sample-superstorecsv

## Steps Included
1. Data Collection
2. Visualizations (scatter, histogram, line)
3. Preprocessing: missing values, IQR outliers, reduction, scaling & discretization
4. Statistical analysis: info/describe, central tendency, dispersion, correlation

## Purpose of the Lab
This lab demonstrates a full exploratory data analysis (EDA) workflow on the **Kaggle Sample Superstore** dataset using Jupyter Notebook. It covers: loading and inspecting data, building exploratory visualizations, handling missing values, detecting/removing outliers, reducing data size, scaling and discretizing features, and computing key statistical measures to inform downstream modeling or business insights.

## Key Insights from Visualizations & Statistics
- **Sales vs. Discount (scatter):** A visible downward trend suggests that **higher discounts are associated with lower realized sales amounts per order** (likely due to reduced unit revenue), even though discounts may increase order frequency.
- **Sales Distribution (histogram/box plots):** Sales are **right-skewed with a long tail**; a small number of orders contribute disproportionately high revenue. IQR-based filtering reduced extreme outliers, making central tendency and dispersion metrics more stable.
- **Sales Over Time (line):** Aggregated daily sales indicate **clear variability and possible seasonality** (periodic peaks), implying time-based factors (promotions, holidays, logistics windows).
- **Central Tendency & Dispersion:** After outlier handling, **mean and median converged**, variance and standard deviation decreased, and the **IQR** narrowed—evidence that the distribution became less extreme and more representative.
- **Correlation Matrix:** Strong relationships among numeric features (e.g., **quantity ↔ sales**, and **profit** relating to **discount/sales**) highlight **multicollinearity** and tradeoffs (e.g., discounting can erode profit even if it helps move units).

## Challenges & Decisions
- **Missing Values:** Some fields contained nulls.  
  **Decision:** Imputed **numeric** columns with **mean** and **categorical** columns with **mode** to preserve row count and maintain downstream comparability.
- **Outliers:** Extreme sales values distorted scale-dependent statistics and plots.  
  **Decision:** Used **IQR (1.5×IQR rule)** on `sales` to identify and remove outliers, improving interpretability of summary stats and model readiness.
- **Data Reduction:** The full dataset is large for screenshots and quick iteration.  
  **Decision:** **Sampled 50%** of rows (reproducible seed) and dropped a low-signal column when present (e.g., `postal_code`) to demonstrate dimension reduction without losing core relationships.
- **Scaling & Discretization:** Features were on different scales.  
  **Decision:** Applied **Min–Max scaling** to numeric columns and **binned `sales` into Low/Medium/High** to support categorical analyses and threshold-based reporting.
