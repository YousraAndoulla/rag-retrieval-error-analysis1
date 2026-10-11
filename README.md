# RAG Retrieval Error Analysis

## Overview

This project investigates the relationship between retrieval failures and factual inaccuracies in an AI-powered customer support system using Python and Pandas.

The analysis builds on user-intent segmentation to identify a problem area, construct a contingency table, calculate error rates, and measure the association between retrieval misses and factual errors.

## Objectives

- Analyze user interactions by intent.
- Identify the segment with the highest calculated drop-off measure.
- Compare retrieval status with response error categories.
- Calculate factual error rates for retrieval misses and successful retrievals.
- Measure the association using the Phi coefficient.
- Visualize the results with a heatmap.

## Dataset

The project uses `synthetic_log_file.csv`, a synthetic dataset containing simulated customer-support interactions.

| Column | Description |
|---|---|
| `user_id` | User identifier |
| `user_intent` | Intent behind the interaction |
| `timestamp` | Date and time of the interaction |
| `retrieval_status` | Retrieval outcome: miss or success |
| `error_category` | Response outcome, such as factual inaccuracy or no error |

## Tools and Technologies

- Python
- Pandas
- NumPy
- Seaborn
- Matplotlib
- Google Colab / Jupyter Notebook

## Methodology

1. Load and inspect the dataset.
2. Group interactions by user intent.
3. Calculate an activity-based drop-off measure.
4. Filter the selected user-intent segment.
5. Create a contingency table using `pd.crosstab()`.
6. Normalize the table to compare error percentages.
7. Calculate the Phi coefficient using a 2×2 table.
8. Visualize the contingency table using a heatmap.

## Results

For the selected `support` segment:

| Retrieval status | Factual inaccuracy | No error | Total |
|---|---:|---:|---:|
| Miss | 77 | 69 | 146 |
| Success | 50 | 793 | 843 |

### Factual inaccuracy rates

- **Retrieval miss:** 52.7%
- **Successful retrieval:** 5.9%

The Phi coefficient is approximately **0.496**, indicating a positive association between retrieval misses and factual inaccuracies in this segment.

These findings suggest that retrieval failures deserve further investigation. They do not independently establish causation.

## Conclusion

This project demonstrates how data analysis can help investigate possible causes of AI hallucinations. Contingency tables, normalized error rates, and association metrics provide evidence that can guide engineering teams toward investigating retrieval quality before assuming that model retraining is necessary.

**Note:** The dataset is synthetic, and the drop-off calculation is an activity-based measure rather than a standard cohort-retention metric.
