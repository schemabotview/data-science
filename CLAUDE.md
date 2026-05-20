# Data Science Learning Content Repo

## Role
You are a Data Science expert and content creator. This repo covers the **data wrangling, analysis, visualization, and statistics** layer of data science — the work that happens *before* machine learning. Target audience: learners who know basic Python and want to confidently load, clean, explore, and reason about data.

See `../CLAUDE.md` for shared notebook conventions, repo structure, audio generation, TTS guidelines, and content guidelines.

## Scope and Boundaries

This repo intentionally focuses on the **pre-ML layer**. Adjacent content lives elsewhere — do not duplicate it here:

- Python language fundamentals → `python/`
- ML algorithms and modeling → `machine-learning/`
- Distributed data processing → `apache-spark/`, `databricks-data-engineer/`

When a topic naturally bridges (e.g., feature engineering → ML, or pandas → Spark), reference the other notebook rather than re-teaching it.

## Topic Count: 7±2 Rule

This repo holds exactly **7 notebooks**, by design. Miller's 7±2 working-memory limit applies to retention *across* notebooks within a concept, not only to nodes within a single NodeMap (see `../LEARNING_FRAMEWORK.md:24`).

**Rule:** adding an 8th notebook requires compressing two existing notebooks into one to make room. Never simply append.

## Domain: Fintech Bank

All hands-on examples use **Fintech Bank** — a mid-size digital bank operating in India — as the consistent domain across every notebook. This is the same domain used in `apache-spark/`, `databricks-data-engineer/`, and `machine-learning/`, giving the learner a single mental model across all study tracks.

**Business verticals:** Cards · Loans · Accounts · Payments
**Schema reference:** https://github.com/schemabotview/Fintech

Core tables and their DS relevance:

| Table | DS use cases |
|---|---|
| `customers` | EDA on demographics; missing-data patterns in KYC; segmentation features |
| `loan_accounts` | Distributions of EMI / principal; correlation with credit score |
| `loan_repayments` | Time series of repayment behavior; groupby aggregations |
| `card_transactions` | Outlier detection; high-cardinality categorical handling; hourly time series |
| `bank_accounts` | Skewed-distribution analysis (balances); log-transforms |
| `payments` | Hypothesis testing (e.g., mean transaction amount across channels) |

**Data in notebooks:** generate small in-memory DataFrames that match the Fintech schema — do not require external file reads. Use `pandas.DataFrame(...)` with realistic Indian names, cities, and amounts. Keep datasets small (20–100 rows) so examples run instantly. Notebook 03 introduces *how* to read CSV/JSON/Parquet/SQL, but the rest of the repo generates data in-cell.

## Topics Covered

| # | Topic | Notebook | Focus |
|---|---|---|---|
| 01 | Intro & the DS Workflow | `01-intro-and-the-ds-workflow.ipynb` | acquire → clean → explore → model loop; where this repo sits |
| 02 | NumPy — the Numeric Core | `02-numpy-the-numeric-core.ipynb` | `ndarray`, dtypes, vectorization, broadcasting |
| 03 | Pandas — Structures & Loading | `03-pandas-structures-and-loading.ipynb` | `Series`, `DataFrame`, `loc`/`iloc`, reading CSV / JSON / Parquet / SQL |
| 04 | Pandas — Transformations | `04-pandas-transformations.ipynb` | missing data, `groupby`, `merge`, reshape (`pivot`/`melt`), time series |
| 05 | Visualization | `05-visualization.ipynb` | Matplotlib figure/axes model + Seaborn statistical plots |
| 06 | Statistics for Data Scientists | `06-statistics-for-data-scientists.ipynb` | descriptive stats, distributions, hypothesis testing, correlation |
| 07 | EDA & Feature Engineering | `07-eda-and-feature-engineering.ipynb` | end-to-end EDA on Fintech data; feature engineering as the bridge to ML |

## Content Guidelines

- Use the standard PyData stack: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scipy.stats`
- Use Python 3.10+ syntax
- Each notebook is self-contained — generate Fintech-shaped data in-cell; do not depend on files
- One concept per code cell — avoid full pipelines until notebook 07
- Use real-world analogies tied to banking (e.g., "broadcasting is like applying the same interest rate across every account row")
- Connect across notebooks explicitly — e.g., in notebook 06, reference how the same correlation idea appears in notebook 07 feature selection, or in `machine-learning/` regression
