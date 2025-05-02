# Assessing-Professor-Effectiveness
Principles of Data Science II - Capstone Project

In this project, I explored the relationships between professor characteristics and their ratings on RateMyProfessors.com. Using two datasets — one containing quantitative measures (ratings, difficulty, number of ratings, gender, etc.) and the other containing qualitative information (university, state, major) — I merged, cleaned, and analyzed the data to uncover patterns in how professors are rated, and what factors contribute to their "hotness" (pepper) designation.

## Dataset Description
The project uses two datasets:

1. Numerical Data (rmpCapstoneNum.csv):
    - Contains:
         - Average Ratings
         - Average Difficulty
         - Number of Ratings
         - Pepper status (Hotness, binary)
         - Retake Percent
         - Online Ratings
         - Gender (Male/Female indicator)

  2. Qualitative Data (rmpCapstoneQual.csv):
       - Contains: 
          - Major
          - University Name
          - State

Both datasets were merged after filtering professors with very few ratings to improve reliability.

## Methodology 
1. Preprocessing:
   - Removed null or invalid rows.
   - Merged numerical and qualitative datasets on index.
   - Thresholded to only keep professors with ≥5 ratings.

2. Exploratory Data Analysis (EDA)
   - Examined distributions of ratings across genders and modalities (online vs in-person).
   - Analyzed pepper rates across universities.

3. Statistical Testing
   - Mann-Whitney U Tests for non-normally distributed comparisons (e.g., gender differences, online vs in-person ratings, hot vs non-hot professors).
   - Spearman Correlation for rating vs difficulty relationship.
   - Ordinary Least Squares (OLS) Regression for continuous variable relationships (e.g., experience vs rating).

4. Classification Modeling
   - Logistic Regression models to predict whether a professor gets a "pepper" using:
       - Only Average Ratings (baseline model)
       - All available factors (full model)
       - Checked Variance Inflation Factors to address multicollinearity

## Models Built

| Model Description                         | Metric                     | Performance |
|:------------------------------------------|:---------------------------|:------------|
| Logistic Regression (Average Rating Only) | Area Under ROC Curve (AUROC) | 0.78        |
| Logistic Regression (All Factors)         | Area Under ROC Curve (AUROC) | 0.79        |
| OLS Regression (Difficulty Only)          | R-squared                   | 0.38        |
| OLS Regression (All Factors)              | R-squared                   | 0.799       |

## Key Findings
- Gender Bias:
  - Male professors had a slightly higher median rating (4.2) compared to female professors (4.1).
  - The difference was statistically significant (Mann-Whitney U test, p < 0.05).

- Online Classes Impact:
  - Professors who taught more online classes had lower ratings compared to those teaching mostly in-person (Median: 3.8 vs 4.1).

- Difficulty vs Ratings:
  - There was a strong negative correlation between Average Difficulty and Average Ratings (Spearman ρ = -0.6).

- Retake Percent Influence:
  - Retake Percent strongly positively correlated with Average Ratings (Correlation = 0.88).

- Professor "Hotness" and Ratings:
  - Hot professors had significantly higher median ratings (4.5) compared to non-hot professors (3.6).

- Predictive Models:
  - Using only Average Ratings gave an AUROC of 0.78.
  - Using all features improved AUROC slightly to 0.79, suggesting that most of the predictive power comes from the average rating alone.

- Top Universities with Highest Hotness Rates:
  - Community College of Philadelphia had the highest pepper rate (85%).
  - Other top universities included Los Angeles Southwest College and College of the Sequoias.



