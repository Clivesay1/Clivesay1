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
