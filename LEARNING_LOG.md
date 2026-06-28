## Learning Log — April 26, 2026

Reviewing feature engineering techniques for the MTG value model. Interaction terms between EDHREC rank and set age improve R² by about 0.02 — small but meaningful.

Also experimenting with log-transforming price targets to handle the right-skewed distribution of card prices. Most cards cluster under $5, with a long tail of expensive staples.

## 2026-04-27 11:42
Used scipy.stats for Mann-Whitney U tests — non-parametric test appropriate for comparing price distributions between card rarities.

## April 28, 2026
Studied seaborn's FacetGrid for multi-panel visualizations. Faceting by category (e.g., rarity tier, genre) is more informative than overlapping distributions in a single plot.

## April 30, 2026
Studied matplotlib's object-oriented interface (Figure and Axes objects) vs. pyplot state machine. OO interface is more flexible for complex multi-panel figures. Converting all project charts to use explicit Axes objects.

## May 02, 2026

Working through the MTG value model today — specifically the reprint risk component. It's tricky to quantify because reprints are announced suddenly and can drop prices 40-60% overnight. Using a combination of time-since-last-print and current price-to-historical-average ratio as a proxy.

## May 04, 2026

- Built correlation heatmaps with seaborn — mask upper triangle for cleaner look
- Used annot=True with fmt='.2f' for readable correlation values
- Diverging palette (coolwarm) works best for correlation matrices

## May 5, 2026

Comparing Random Forest vs. Gradient Boosting for the MTG price prediction model.
Results on holdout set:
- Random Forest: RMSE $4.21, R² 0.68, training time 12s
- Gradient Boosting (XGBoost): RMSE $3.87, R² 0.72, training time 34s
- Ridge Regression (baseline): RMSE $6.14, R² 0.51

XGBoost wins on accuracy but Random Forest is more interpretable.
Going with Random Forest for the portfolio project — explainability matters
more than marginal accuracy improvement for a portfolio showcase.

## May 2026 Update

Reviewed pandas groupby + agg patterns for multi-metric summaries. Using named aggregations (pd.NamedAgg) makes the resulting DataFrame columns self-documenting.

## May 19, 2026
Exploring model interpretability tools: feature_importances_ from Random Forest gives a quick ranking. Permutation importance (sklearn.inspection) is more reliable — measures actual impact on model performance. SHAP values give per-prediction explanations — useful for portfolio projects to show hiring managers you understand not just accuracy but WHY the model works. Adding a SHAP summary plot to the MTG project notebook.

## May 25, 2026

Studied scipy.stats for non-parametric hypothesis testing. Mann-Whitney U test is appropriate for comparing price distributions between card rarity tiers — more robust than t-test given the skewed distributions.

## May 28, 2026
Refining git workflow for data analysis projects. Using `.gitignore` to exclude large raw data files (>50MB) and keeping only processed/summary data in the repo. Committing notebooks with outputs cleared (`jupyter nbconvert --clear-output`) to avoid large diffs. Using descriptive commit messages that reference the analysis section: 'add Part 3 risk-adjusted return analysis' is more informative than 'update notebook'. Tagging major milestones with `git tag v1.0-eda` for easy reference.

## May 31, 2026 — Data Cleaning Workflow
Documenting data cleaning checklist for portfolio projects: (1) Check dtypes immediately after load — fix before any analysis. (2) Use `df.isna().sum()` to quantify missing data before deciding on imputation strategy. (3) For price data: log-transform before modeling (right-skewed distributions). (4) Outlier detection: IQR method for bounded data, z-score for normally distributed. (5) Always validate cleaned data against known values (e.g., check that S&P 500 CAGR ≈ 10% over 20yr). Document every cleaning decision in markdown cells.

<!-- 2026-06-01 15:43 -->
> Log: reviewed confusion matrix interpretation.

---

## 2026-06-07

**Topic:** Writing analysis summaries for non-technical audiences

Practiced translating model outputs into plain language. Instead of 'the R² is 0.73', write 'the model explains 73% of the variation in card prices.' Lead with the business insight, then support with the metric. Stakeholders care about the implication, not the statistic.

---

## Learning Log — Statistics

**Date:** June 16, 2026

### Today's Focus
- Reviewed Pearson vs Spearman correlation — Spearman better for non-normal distributions
- Shapiro-Wilk test for normality: p > 0.05 suggests normal distribution
- Log transformation to normalize right-skewed price data
- Bootstrapping for confidence intervals when sample size is small

## Learning Log — Data Cleaning
**Date:** June 19, 2026

### Today's Focus
- Handling missing data: MCAR, MAR, MNAR — different imputation strategies
- Outlier detection: IQR method vs Z-score vs isolation forest
- String cleaning with regex: extracting structured data from messy text
- Pandas: apply() vs vectorized operations — performance comparison

## June 28, 2026
Reviewed statistical hypothesis testing: t-tests, Mann-Whitney U, chi-square, and ANOVA. Mann-Whitney U is appropriate for non-normal distributions (price data is always right-skewed). Using it to test whether median card prices differ significantly between rarity tiers in the MTG dataset.
