# Pokémon Legendary Classification Project

## Project Objective
The goal of this project is to explore Pokémon attributes (base stats, types, and generations)
to understand what differentiates Legendary Pokémon from non-Legendary ones, and to build a
predictive model that classifies Legendary status using base stats.

## Dataset
- Source: Pokémon dataset containing base stats, typing, generation, and Legendary status
- Rows: ~1,070 Pokémon
- Target variable: `legendary` (True / False)

### Key Features Used
- HP
- Attack
- Defense
- Special Attack
- Special Defense
- Speed

## Data Cleaning & Validation
- Corrected Generation `0` entries (Meltan & Melmetal) by assigning them to Generation 7
- Standardized categorical values (types)
- Validated generation values to ensure consistency
- Converted `generation` to a categorical variable for analysis

## Exploratory Data Analysis (EDA)
- Compared stat distributions between Legendary and Non-Legendary Pokémon
- Analyzed correlations between base stats using a heatmap
- Examined stat differences across Pokémon types
- Visualized Attack vs Defense relationships with Legendary status overlays

### Key EDA Insight
Legendary Pokémon consistently exhibit higher offensive and speed-related stats, while defensive
stats show more overlap with non-Legendary Pokémon.

## Modeling Approach
**Model:** Logistic Regression  
**Task:** Binary classification (Legendary vs Non-Legendary)

### Modeling Details
- Train/test split with stratification (70/30)
- Addressed class imbalance using `class_weight="balanced"`
- Features scaled implicitly by model coefficients (linear model)

### Performance
- ROC AUC: **~0.97**
- Strong overall discrimination despite class imbalance
- Recall for Legendary Pokémon improved via class weighting

## Model Interpretation
Feature importance analysis shows:
- **Special Attack** and **Speed** are the strongest predictors of Legendary status
- Offensive capabilities are more indicative than defensive stats

## Statistical Testing
- Conducted a two-sample t-test on Attack stats
- Result: Legendary Pokémon have significantly higher Attack values  
  *(p < 0.001)*

This supports both the EDA findings and the model’s learned relationships.

## Key Takeaways
- Legendary Pokémon significantly outperform non-Legendary Pokémon in offensive and speed stats
- Generation alone is not a strong predictor of Legendary status
- A simple, interpretable logistic regression model achieved strong predictive performance
- Proper handling of class imbalance is critical when modeling rare classes

## Tools & Libraries
- Python
- Pandas
- NumPy
- Seaborn / Matplotlib
- Scikit-learn
- SciPy

## Key Takeaways
- Offensive capability is the most informative predictor of Legendary status
- Generation alone is weak signal → matches franchise design (Legendaries appear across gens)
- Balanced class weighting is critical for rare-class recall
- High performance achieved with simple, interpretable models
