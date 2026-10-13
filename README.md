# Retail Store Performance Analysis and Sales Prediction

**Project by:** Maanveer Singh
**Program:** AICTE | IBM SkillsBuild Data Analytics with AI Academic Internship 2026 | BharatCares

**Repository:** https://github.com/Manveer1806/store_performance_analysis

## Project Description

This project analyzes store-level data from a supermarket chain (896 stores) to understand how store size, stock range and customer traffic relate to store sales. It measures how efficiently each store uses its floor space, groups stores into segments with K-Means clustering, and tests whether machine learning can predict store sales from the available data.

## Problem Statement

Sales vary widely across stores, but it is not clear what drives the differences. The project answers four questions:

1. How do store area, items available and daily customer count relate to store sales?
2. Which stores are the most and least efficient in turning floor space into revenue?
3. Can stores be grouped into meaningful segments for planning?
4. Can a regression model predict store sales from store characteristics?

## Dataset

- **Source:** Kaggle, *Supermarket Store Branches Sales Analysis* by surajjha101: https://www.kaggle.com/datasets/surajjha101/stores-area-and-sales-data
- **File used in this project:** `Use_Stores.csv`
- **Size:** 896 stores, 5 columns, no missing values
- **Columns:**

| Column | Description |
|---|---|
| Store ID | Unique store identifier (1 to 896) |
| Store_Area | Physical store area (square yards) |
| Items_Available | Number of different items stocked |
| Daily_Customer_Count | Average customers visiting per day |
| Store_Sales | Store sales (US dollars) |

## Technologies Used

- Python 3.10+
- pandas and NumPy: data loading, cleaning and feature engineering
- Matplotlib and Seaborn: data visualization
- SciPy: statistical tests (Pearson, Spearman, ANOVA, Kruskal-Wallis)
- scikit-learn: K-Means clustering, regression models, cross-validation
- Jupyter Notebook: analysis environment

## Steps Used for Analysis

1. Load the data and fix file quirks (hidden BOM character, trailing space in a column name).
2. Check data quality: missing values, duplicates, invalid values.
3. Engineer KPIs: sales per sq yd, sales per customer, customers per 100 sq yd, items per sq yd, store size groups.
4. Explore distributions and detect outliers with the IQR method.
5. Analyze correlations and test them statistically.
6. Compare store size groups and customer traffic groups.
7. Rank the most and least space-efficient stores.
8. Segment stores with K-Means clustering (elbow method and silhouette score).
9. Train and compare regression models with 5-fold cross-validation and a hold-out test set.
10. Run robustness checks and turn the results into business recommendations.

## Key Findings

| Question | Finding |
|---|---|
| Average store sales | USD 59,351 (middle 50% of stores: USD 46,530 to USD 71,872) |
| Area vs sales correlation | 0.097 (very weak) |
| Customer count vs sales correlation | 0.009 (no relationship) |
| Area vs items available correlation | 0.999 (items are about 1.2 per sq yd everywhere) |
| Sales per sq yd: Small vs Extra Large stores | USD 50.5 vs USD 34.0 |
| Best store segment | High-Yield Stores: USD 58.7 per sq yd vs about USD 35 for other segments |
| Predictive models | No model meaningfully beat the mean baseline (cross-validated R-squared about 0) |

Main insight: store size and footfall explain almost none of the difference in sales. Space efficiency matters more than size or traffic.

## Setup / Run Instructions

1. Clone or download this repository:
   ```bash
   git clone https://github.com/Manveer1806/store_performance_analysis.git
   cd store_performance_analysis
   ```
2. (Optional) Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate        # Windows: venv\Scripts\activate
   ```
3. Install the required libraries:
   ```bash
   pip install -r requirements.txt
   ```
4. Make sure `Use_Stores.csv` is in the same folder as the notebook.
5. Open and run the notebook:
   ```bash
   jupyter notebook Maanveer_Singh_Store_Performance_Analysis.ipynb
   ```
6. Choose **Kernel > Restart & Run All**. A `charts/` folder with all figures is created automatically.

## Project Files

- `Maanveer_Singh_Store_Performance_Analysis.ipynb`: main analysis notebook
- `requirements.txt`: Python dependencies
- `Maanveer_Singh_ProjectReport.docx`: full project report
- `Use_Stores.csv`: dataset used for analysis
- `README.md`: this file

## Business Recommendations

- Do not expand floor space to grow sales; compact stores earn more per sq yd.
- Study the High-Yield segment and copy its pricing, range and layout practices.
- Review the least efficient stores for layout, range or space changes.
- Look beyond footfall: test basket-building ideas and track basket value, since busier stores do not earn more.
- Collect richer data (location, pricing, basket value, promotions) to make sales prediction possible.

## Conclusion

Store area and customer count alone cannot predict store sales, which shows that the real sales drivers are not captured in this dataset. The analysis still gives clear, usable results: which store sizes waste space, which stores to learn from, which to fix, and four store segments for targeted planning.
