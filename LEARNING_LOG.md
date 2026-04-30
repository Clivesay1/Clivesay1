## Learning Log — April 26, 2026

Reviewing feature engineering techniques for the MTG value model. Interaction terms between EDHREC rank and set age improve R² by about 0.02 — small but meaningful.

Also experimenting with log-transforming price targets to handle the right-skewed distribution of card prices. Most cards cluster under $5, with a long tail of expensive staples.

## 2026-04-27 11:42
Used scipy.stats for Mann-Whitney U tests — non-parametric test appropriate for comparing price distributions between card rarities.

## April 28, 2026
Studied seaborn's FacetGrid for multi-panel visualizations. Faceting by category (e.g., rarity tier, genre) is more informative than overlapping distributions in a single plot.

## April 30, 2026
Studied matplotlib's object-oriented interface (Figure and Axes objects) vs. pyplot state machine. OO interface is more flexible for complex multi-panel figures. Converting all project charts to use explicit Axes objects.
